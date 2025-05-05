---
title: Gargalo de alta carga do MySQL no Adobe Commerce na infraestrutura em nuvem
description: Este tópico discute uma solução quando a alta carga do MySQL causa um problema de gargalo de desempenho no Adobe Commerce na infraestrutura em nuvem.
exl-id: c1f9d282-41d8-4850-8a24-336d55aa3140
feature: Cloud, Observability, Paas, Services
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
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
* Serviço de APM da New Relic (**A conta da infraestrutura em nuvem do Adobe Commerce inclui o software para o serviço de APM da New Relic**, juntamente com uma chave de licença.)

Para obter mais informações sobre o serviço APM da New Relic e sua configuração com a conta do Adobe Commerce na infraestrutura em nuvem, vá para [New Relic Services](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/monitor/new-relic/new-relic-service) e [Introdução ao APM da New Relic](https://docs.newrelic.com/docs/apm/new-relic-apm/getting-started/introduction-apm/).

## Problema

<u>Etapas Para Ver Se O Problema Afeta Você</u>

1. No Gráfico de Visão Geral de APM do New Relic, verifique a primeira indicação de que o MySQL se tornou um gargalo. Veja a imagem de amostra abaixo onde o MySQL se tornou um gargalo e ocupa a maior parte do tempo das transações Web:

   ![KB-372_image002.png](assets/KB-372_image002.png)

   Observe como a linha tracejada vermelha na imagem mostra uma tendência ascendente discernível no tempo de transações Web MySQL e, em seguida, atinge níveis ainda mais altos.
1. Daqui você pode ir para a tela do **Banco de Dados**, onde pode ver a segunda indicação de alta taxa de transferência ou lentidão de consultas `SELECT` no MySQL, e na imagem de exemplo abaixo, você pode ver ao classificar por **Mais demorado**, seu armazenamento, neste exemplo, está lento em `SELECT` consultas do MySQL.

   ![KB-372_image003_BlurredExtension.png](assets/KB-372_image003_BlurredExtension.png)

Analise as transações lentas no APM do New Relic. Se você vir um alto volume de consultas ou alta pressão em um banco de dados MySQL, é possível espalhar a carga em diferentes nós habilitando `SLAVE` conexões.

## Causa

Seu Adobe Commerce no repositório de infraestrutura na nuvem tem alta taxa de transferência ou está lento em consultas MySQL `SELECT`.

## Solução

>[!WARNING]
>
>Para arquitetura escalonada (arquitetura dividida), as conexões secundárias Redis **NÃO DEVEM** estar habilitadas. Você pode verificar se está na arquitetura dimensionada acessando a URL do projeto, por exemplo, `https://console.adobecommerce.com/<owner-user-name>/<project-ID>/<environment-name>`. Clique em **[!UICONTROL SSH]**. Se houver mais de três nós, você estará em uma arquitetura escalonada. Se você ativar as leituras subordinadas Redis na arquitetura escalada, o cliente receberá erros nas conexões Redis que não puderem se conectar. Isso tem a ver com como os clusters são configurados para processar conexões Redis. Os Redis Slaves ainda estão ativos, mas não serão usados para Leituras Redis. Recomendamos a arquitetura dimensionada para usar o Adobe Commerce 2.3.5 ou posterior e implementar uma nova configuração de back-end Redis e implementar o cache L2 para Redis.

Se essas duas indicações estiverem presentes, habilitar `SLAVE` conexões para o banco de dados MySQL e Redis pode ajudar a distribuir a carga entre os diferentes nós.

O Adobe Commerce pode ler vários bancos de dados ou o Redis de forma assíncrona. Atualizando o arquivo `.magento.env.yaml` definindo como `true` os valores `MYSQL_USE_SLAVE_CONNECTION` e `REDIS_USE_SLAVE_CONNECTION` para usar uma conexão **somente leitura** com o banco de dados para receber tráfego somente leitura em um nó não mestre. Isso melhora o desempenho por meio do balanceamento de carga, pois somente um nó precisa lidar com o tráfego de leitura-gravação. Defina como `false` para remover qualquer matriz de conexão somente leitura existente do arquivo `env.php`.

### Etapas

1. Edite o arquivo `.magento.env.yaml` e adicione o seguinte conteúdo:

   ![KB-372_image004.png](assets/KB-372_image004.png)

   Você pode encontrar mais detalhes em [Implantar Variáveis em DevDocs](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy#mysql_use_slave_connection).

1. Confirme suas alterações e envie-as por push.
1. O envio de alterações iniciará um novo processo de implantação. Depois que a implantação for concluída com êxito, sua instância do Adobe Commerce na infraestrutura em nuvem deverá estar configurada para usar conexões subordinadas.

## Perguntas comuns

Abaixo estão as perguntas comuns que você pode fazer ao considerar usar a funcionalidade Conexões Escravas para o seu Adobe Commerce na loja de infraestrutura em nuvem.

* Há algum problema conhecido ou limitação para usar conexões subordinadas? **Não temos problemas conhecidos ao usar Conexões Escravas. Verifique se você está usando o pacote de ferramentas ece atualizado mais recentemente. Há instruções aqui sobre [como atualizar seu pacote ece-tools](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package).**
* Há alguma latência extra usando conexões subordinadas? *Sim, a latência entre AZs (zonas de disponibilidade cruzada) é maior e reduz o desempenho de uma instância de Adobe Commerce na infraestrutura de nuvem caso a instância não esteja sobrecarregada e possa carregar toda a carga. Mas, claramente, se a instância estiver sobrecarregada - master-slave ajudará no desempenho, espalhando a carga no banco de dados MySQL ou Redis em diferentes nós.*

  **Em clusters não sobrecarregados** - **As Conexões Escravos reduzirão o desempenho em 10-15%**, uma das razões pelas quais não é padrão.

  *Mas em clusters sobrecarregados, há um aumento de desempenho porque esses 10 a 15% são atenuados pela redução da carga por tráfego.*
* Devo ativar essas configurações para minha loja? *Se você tiver carga alta ou esperar carga alta no Banco de Dados MySQL ou no Redis, você definitivamente precisa habilitar as Conexões Escravas. Para um cliente comum com tráfego médio, esta configuração **não**&#x200B;é a ideal para ser habilitada.*

## Leitura relacionada

Em nossa documentação do desenvolvedor:

* [Implantar variáveis](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy).
* [Configure a replicação opcional do banco de dados](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/storage/split-db/multi-master-replication).
* [pacote de ferramentas ece](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/package-overview).

>[!NOTE]
>
>Estamos cientes de que este artigo ainda pode conter termos de software padrão da indústria que alguns podem achar racistas, sexistas ou opressivos, e que podem fazer com que o leitor se sinta ferido, traumatizado ou indesejado. O Adobe está trabalhando para remover esses termos de nosso código, documentação e experiências do usuário.
