---
title: Solução de problemas de implantação do Adobe Commerce
description: Implantações travadas e com falha no Adobe Commerce podem ser resolvidas usando a ferramenta Solução de problemas de implantação. Clique em cada pergunta para revelar a resposta em cada etapa da solução de problemas.
exl-id: 5141e079-be61-44c2-8bff-c4b13cb7e07c
feature: Build, Deploy, Support
role: Developer
source-git-commit: d2c37f4465d5ba4f4b4878eae292fa805d1dc45b
workflow-type: tm+mt
source-wordcount: '1007'
ht-degree: 0%

---

# Solução de problemas de implantação do Adobe Commerce

Implantações travadas e com falha no Adobe Commerce podem ser resolvidas usando a ferramenta Solução de problemas de implantação. Clique em cada pergunta para revelar a resposta em cada etapa da solução de problemas.

## Etapa 1 - Verificar se o serviço está em execução {#step-1}

+++**O Adobe Commerce está funcionando no serviço de infraestrutura em nuvem?**

Implantação paralisada - o serviço de infraestrutura em nuvem do Adobe Commerce está ativo? Verifique a [Adobe Commerce Cloud](https://status.adobe.com/products/3350/).

a. SIM - Continue na [Etapa 2](#step-2).\
b. NÃO - manutenção ou paralisações globais. Verifique a duração estimada e as atualizações.

+++

## Etapa 2 - Verificar implantações em outros ambientes {#step-2}

+++**Existem implantações em outros ambientes que estão bloqueando a implantação no ambiente existente?**

Para obter uma lista de atividades em andamento, execute o comando a seguir usando a Magento-Cloud CLI (se você tiver sido adicionado apenas a um projeto de nuvem). **Observação**: verifique se você está usando a versão mais recente da CLI do Magento Cloud. Para obter as etapas, consulte [Atualizar a CLI](https://experienceleague.adobe.com/pt-br/docs/commerce-on-cloud/user-guide/dev-tools/cloud-cli/cloud-cli-overview) no guia do Commerce na Infraestrutura em Nuvem.

```bash
magento-cloud --state=in_progress
```

Para obter uma lista de atividades em andamento, execute o seguinte comando usando a Magento-Cloud CLI (se tiver sido adicionado a vários projetos):

```bash
magento-cloud -p <project-id or project-url> --state=in_progress
```

Para encontrar informações sobre uma atividade de implantação existente (consulte [Verificando o log de implantação se a interface de nuvem tiver um erro de &quot;log recortado&quot;](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/checking-deployment-log-if-the-cloud-ui-shows-log-snipped-error)
para obter detalhes), execute este comando para obter um log em execução dessa atividade:

```bash
magento-cloud activity:log <activity-id> [OPTIONAL: <-p project-id or project-url>]
```

a. SIM - Solucionar problemas de outro ambiente que bloqueia a implantação no ambiente existente. Vá para [Etapa 3](#step-3).

b. NÃO - Solucionar problemas do ambiente atual. Vá para [Etapa 3](#step-3).

+++


## Etapa 3 - Verificar o SSH em todos os nós {#step-3}

+++**SSH bem-sucedido para todos os nós?**

a. SIM - Continue na [Etapa 4](#step-4).\
b. NÃO - [Enviar um tíquete de suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

## Etapa 4 - Verificar todos os serviços em execução {#step-4}

+++**Todos os serviços estão em execução?**

a. SIM - Continue na [Etapa 5](#step-5).\
b. NÃO - [Enviar um tíquete de suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

## Etapa 5 - Verificar a execução do Bitbucket {#step-5}

+++**Usando Bitbucket?**

a. SIM - Verificar [status.bitbucket.com](https://bitbucket.status.atlassian.com/).\
b. NÃO - Verifique os erros do log de implantação nos [Logs de compilação e implantação](https://experienceleague.adobe.com/pt-br/docs/commerce-on-cloud/user-guide/develop/test/log-locations). Vá para a [Etapa 6](#step-6).

+++

## Etapa 6 - Verificar códigos de erro {#step-6}

+++**Código de erro relatado?**

a. SIM - Continue na [Etapa 7](#step-7).\
b. NÃO - Continue na [Etapa 8](#step-8).

+++

## Etapa 7 - 403 Erro proibido {#step-7}

+++**403 Proibido?**

a. SIM - Continue na [Etapa 16](#step-16).
b. NÃO - Continue na [Etapa 9](#step-9).

+++

## Etapa 8 - Verificar trabalhos cron em execução {#step-8}

+++**Os trabalhos do cron estão em execução no momento?** Faça logon por ssh na ramificação e execute `ps aufxx |grep cron`.

a. SIM - Faça logon por ssh na ramificação afetada (por exemplo, principal). Eliminar e desbloquear trabalhos cron. Isso eliminará as tarefas do cron e redefinirá o status. Execute `php vendor/bin/ece-tools cron:kill` e depois `php vendor/bin/ece-tools cron:unlock`. Se você estava em processo de mesclar um ambiente em outro, verifique se os dois ambientes estão executando crons.\
b. NÃO - Continue na [Etapa 17](#step-17).

+++

## Etapa 9 - Erro de aplicativo implantável no cluster remoto {#step-9}

+++**Não é possível carregar o aplicativo para o erro de cluster remoto?**

a. SIM - Continue na [Etapa 10](#step-10).\
b. NÃO - Continue na [Etapa 11](#step-11).

+++

## Etapa 10 - Verificar armazenamento suficiente {#step-10}

+++**Armazenamento disponível ok?**

* [Verificar ambiente de Integração/Início](https://experienceleague.adobe.com/pt-br/docs/commerce-on-cloud/user-guide/develop/storage/manage-disk-space?lang=en#check-integration-environment)
* [Verificar ambiente de Preparo/Produção Profissional](https://experienceleague.adobe.com/pt-br/docs/commerce-on-cloud/user-guide/develop/storage/manage-disk-space?lang=en#check-dedicated-clusters)

a. SIM - Continue com a [Etapa 11](#step-11).\
b. NÃO - Revise [Gerenciar espaço em disco](https://experienceleague.adobe.com/pt-br/docs/commerce-on-cloud/user-guide/develop/storage/manage-disk-space).

+++

## Etapa 11 - Verificar espaço em disco {#step-11}

+++**_Não foi possível gravar o arquivo Aviso _?**

a. SIM

* Para ambientes de integração/Início:

   * [Aumente o valor do disco em .magento.app.yaml](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space.html?lang=pt-BR#application-disk-space) e reimplante. Se isso não funcionar, [envie um tíquete de suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).
   * Como alternativa, revise a pasta `var/log` e exclua todos os arquivos de log com mais de 1 MB. Execute este comando para verificar os tamanhos dos arquivos:

     ```bash
     ls -la var/log
     ```

* Para ambientes de preparo/produção profissionais:

   1. Envie um tíquete de suporte para adicionar armazenamento.

b. NÃO - Continue com a [Etapa 12](#step-12).

+++

## Etapa 12 - Erro de falha na reimplantação do ambiente {#step-12}

+++**Erro de falha na reimplantação do ambiente?**

a. SIM - Continue com a [Etapa 13](#step-13).\
b. NÃO - Continue com a [Etapa 8](#step-8).

+++

## Etapa 13 - Verificar falha de atualização do Elasticsearch {#step-13}

+++**Elasticsearch sendo atualizado ou implantado?**

a. SIM - falha nas etapas de atualização do Elasticsearch. Consulte [compatibilidade de software do Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/setup-upgrade.html). Se a atualização do Elasticsearch ainda não funcionar, [envie um tíquete de suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket). **Observação**: no Adobe Commerce na infraestrutura em nuvem, esteja ciente de que as atualizações de serviço não podem ser enviadas para o ambiente de produção sem aviso prévio de 48 horas úteis para nossa equipe de infraestrutura. Isso é necessário, pois precisamos garantir que tenhamos um engenheiro de suporte de infraestrutura disponível para atualizar sua configuração dentro do prazo desejado com tempo de inatividade mínimo para seu ambiente de produção. Portanto, 48 horas antes de quando suas alterações precisam estar em produção, [envie um tíquete de suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) detalhando a atualização de serviço necessária e informando a hora em que deseja que o processo de atualização tenha início.\
b. NÃO - Continue na [Etapa 14](#step-14).

+++

## Etapa 14 - Verificar limites de espaço {#step-14}

+++**Sistema de arquivos sem inodes ou espaço?**

a. SIM - Consulte [Gerenciar espaço em disco](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space.html?lang=pt-BR#application-disk-space).\
b. NÃO - Continue na [Etapa 15](#step-15).

+++

## Etapa 15 - Erro de versão do Elasticsearch {#step-15}

+++**Erro sobre as versões de Elasticseach?**

a. SIM - Continue na [Etapa 16](#step-16).\
b. NÃO - Continue na [Etapa 21](#step-21).

+++

## Etapa 16 - Verificar configuração do Composer {#step-16}

+++**Configuração correta do compositor?**

a. SIM - Continue na [Etapa 10](#step-10).\
b. NÃO - Revise a [página da Web de solução de problemas do Composer](https://getcomposer.org/doc/articles/troubleshooting.md).

+++

## Etapa 17 - Verificar processos de longa execução {#step-17}

+++**Processos de longa execução?**

a. SIM - Identificar processos de longa duração e, em seguida, eliminar processos:
1. Execute o seguinte comando no terminal: `ps aufx`.
1. Localize o PID do processo de longa duração.
1. Encerrar o processo usando `kill -9 <PID>`.

Monitore implantações para recorrência.

b. NÃO - Continue na [Etapa 18](#step-18).

+++

## Etapa 18 - Verificar falha do gancho de postagem {#step-18}

+++**Falha/travamento do gancho de postagem?**

a. SIM - Banco de Dados: [Espaço livre em disco](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space.html?lang=pt-BR#allocate-disk-space), corrompido, tabelas incompletas/corrompidas.\
b. NÃO - Continue na [Etapa 19](#step-19).

+++

## Etapa 19 - Verificar se extensões de terceiros bloqueiam a implantação {#step-19}

+++**Usando extensões de terceiros?**

a. SIM - Tente [desabilitar as extensões de terceiros](https://experienceleague.adobe.com/pt-br/docs/commerce-on-cloud/user-guide/configure-store/extensions) e executar a implantação (para ver se elas são a causa do problema), especialmente se houver nomes de extensão em quaisquer erros.\
b. NÃO - Continue na [Etapa 20](#step-20).

+++

## Etapa 20 - Verificar consultas lentas {#step-20}

+++**Consultas de longa duração?**

[Verificar log de consulta lenta e show processlist do MySQL](/help/troubleshooting/database/checking-slow-queries-and-processes-mysql.md).

a. SIM - Elimine consultas de longa execução. Revisar [Sintaxe de eliminação do MySQL.](https://dev.mysql.com/doc/refman/8.0/en/kill.html)\
b. NÃO - [Enviar um tíquete de suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

## Etapa 21 - Fazer downgrade da versão do Elasticsearch {#step-21}

+++**Rebaixando versões do Elasticsearch?**

a. SIM - não pode ser feito por meio de configuração. [Enviar um tíquete de suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
b. NÃO - [Enviar um tíquete de suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

[Voltar à Etapa 1](#step-1)
