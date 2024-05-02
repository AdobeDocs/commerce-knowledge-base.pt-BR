---
title: Gargalo de alta carga do MySQL no Adobe Commerce na infraestrutura em nuvem
description: Este tópico discute uma solução quando a alta carga do MySQL causa um problema de gargalo de desempenho no Adobe Commerce na infraestrutura em nuvem.
exl-id: c1f9d282-41d8-4850-8a24-336d55aa3140
feature: Cloud, Observability, Paas, Services
role: Developer
source-git-commit: 075f55b94202f75839abd25bd47824eeb5226485
workflow-type: tm+mt
source-wordcount: '864'
ht-degree: 0%

---

# Gargalo de alta carga do MySQL no Adobe Commerce na infraestrutura em nuvem

Este tópico discute uma solução quando a alta carga do MySQL causa um problema de gargalo de desempenho no Adobe Commerce na infraestrutura em nuvem.

## Produtos e versões afetados

* Contas Pro do Adobe Commerce na infraestrutura em nuvem 2.x.x.

### Pré-requisitos

* Ferramentas ECE versão 2002.0.16 e superior
* Serviço APM da New Relic (**Sua conta do Adobe Commerce na infraestrutura em nuvem inclui o software para o serviço APM da New Relic** juntamente com uma chave de licença.)

Para obter mais informações sobre o serviço APM da New Relic e sua configuração com sua conta do Adobe Commerce na infraestrutura em nuvem, acesse [Serviços da New Relic](https://devdocs.magento.com/guides/v2.3/cloud/project/new-relic.html) e [Introdução ao APM do New Relic](https://docs.newrelic.com/docs/apm/new-relic-apm/getting-started/introduction-apm/).

## Problema

<u>Etapas Para Ver Se O Problema Afeta Você</u>

1. No Gráfico de Visão Geral de APM do New Relic, verifique a primeira indicação de que o MySQL se tornou um gargalo. Veja a imagem de amostra abaixo onde o MySQL se tornou um gargalo e ocupa a maior parte do tempo das transações Web:

   ![KB-372_image002.png](assets/KB-372_image002.png)

   Observe como a linha tracejada vermelha na imagem mostra uma tendência ascendente discernível no tempo de transações Web MySQL e, em seguida, atinge níveis ainda mais altos.
1. A partir daqui, você pode ir para o seu **Banco de dados** tela onde você pode ver a segunda indicação de alta taxa de transferência ou baixa `SELECT` consultas no MySQL e na imagem de amostra abaixo, é possível ver ao classificar por **Mais demorado**, sua loja, neste exemplo, está lenta `SELECT` Consultas MySQL.

   ![KB-372_image003_BlurredExtension.png](assets/KB-372_image003_BlurredExtension.png)

Analise as transações lentas no APM do New Relic. Se você vir um alto volume de consultas ou alta pressão em um banco de dados MySQL, é possível espalhar a carga em diferentes nós habilitando `SLAVE` conexões.

## Causa

Seu Adobe Commerce na loja de infraestrutura em nuvem tem alta taxa de transferência ou está lento `SELECT` Consultas MySQL.

## Solução

>[!WARNING]
>
>Para arquitetura dimensionada (arquitetura dividida), as conexões secundárias do Redis **NÃO DEVE** ser ativado. Você pode verificar se está em arquitetura dimensionada acessando o URL do projeto, por exemplo, `https://console.adobecommerce.com/<owner-user-name>/<project-ID>/<environment-name>`. Clique em **[!UICONTROL SSH]**. Se houver mais de três nós, você estará em uma arquitetura escalonada. Se você ativar as leituras subordinadas Redis na arquitetura escalada, o cliente receberá erros nas conexões Redis que não puderem se conectar. Isso tem a ver com como os clusters são configurados para processar conexões Redis. Os Redis Slaves ainda estão ativos, mas não serão usados para Leituras Redis. Recomendamos a arquitetura dimensionada para usar o Adobe Commerce 2.3.5 ou posterior e implementar uma nova configuração de back-end Redis e implementar o cache L2 para Redis.

Se essas duas indicações estiverem presentes, habilite `SLAVE` As conexões do banco de dados MySQL e do Redis podem ajudar a distribuir a carga entre os diferentes nós.

O Adobe Commerce pode ler vários bancos de dados ou o Redis de forma assíncrona. Atualização do `.magento.env.yaml` arquivo definindo como `true` os valores `MYSQL_USE_SLAVE_CONNECTION` e `REDIS_USE_SLAVE_CONNECTION` para usar um **somente leitura** conexão com o banco de dados para receber tráfego somente leitura em um nó não mestre. Isso melhora o desempenho por meio do balanceamento de carga, pois somente um nó precisa lidar com o tráfego de leitura-gravação. Defina como `false` para remover qualquer matriz de conexão somente leitura existente do `env.php` arquivo.

### Etapas

1. Editar seu `.magento.env.yaml` e adicione o seguinte conteúdo:

   ![KB-372_image004.png](assets/KB-372_image004.png)

   Você pode encontrar mais detalhes em [Implantar variáveis no DevDocs](https://devdocs.magento.com/cloud/env/variables-deploy.html#mysql_use_slave_connection).

1. Confirme suas alterações e envie-as por push.
1. O envio de alterações iniciará um novo processo de implantação. Depois que a implantação for concluída com êxito, sua instância do Adobe Commerce na infraestrutura em nuvem deverá estar configurada para usar conexões subordinadas.

## Perguntas comuns

Abaixo estão as perguntas comuns que você pode fazer ao considerar usar a funcionalidade Conexões Escravas para o seu Adobe Commerce na loja de infraestrutura em nuvem.

* Há algum problema conhecido ou limitação para usar conexões subordinadas? **Não temos nenhum problema conhecido ao usar conexões subordinadas. Verifique se você está usando o pacote de ferramentas ece atualizado mais recentemente. As instruções estão aqui em [como atualizar seu pacote de ferramentas ece](https://devdocs.magento.com/cloud/project/ece-tools-update.html).**
* Há alguma latência extra usando conexões subordinadas? *Sim, a latência entre AZ (zonas de disponibilidade cruzada) é maior e reduz o desempenho de uma instância do Adobe Commerce na infraestrutura em nuvem, caso a instância não esteja sobrecarregada e possa carregar toda a carga. Mas, claramente, se a instância estiver sobrecarregada - master-slave ajudará no desempenho, espalhando a carga no banco de dados MySQL ou Redis em diferentes nós.*

  **Em clusters não sobrecarregados** -  **As conexões subordinadas reduzirão o desempenho em 10 a 15%**, que é um dos motivos pelos quais não é padrão.

  *Mas em clusters sobrecarregados, há um aumento no desempenho porque esses 10 a 15% são atenuados pela redução da carga por tráfego.*
* Devo ativar essas configurações para minha loja? *Se você tiver carga alta ou esperar carga alta no banco de dados MySQL ou Redis, você definitivamente precisa habilitar as conexões subordinadas. Para um cliente regular com tráfego médio, isso é&#x200B;**não**uma configuração ideal a ser ativada.*

## Leitura relacionada

Em nossa documentação do desenvolvedor:

* [Implantar variáveis](https://devdocs.magento.com/cloud/env/variables-deploy.html).
* [Configurar replicação de banco de dados opcional](https://devdocs.magento.com/guides/v2.3/config-guide/multi-master/multi-master_slavedb.html).
* [pacote ece-tools](https://devdocs.magento.com/cloud/reference/ece-tools-reference.html).

>[!NOTE]
>
>Estamos cientes de que este artigo ainda pode conter termos de software padrão da indústria que alguns podem achar racistas, sexistas ou opressivos, e que podem fazer com que o leitor se sinta ferido, traumatizado ou indesejado. O Adobe está trabalhando para remover esses termos de nosso código, documentação e experiências do usuário.
