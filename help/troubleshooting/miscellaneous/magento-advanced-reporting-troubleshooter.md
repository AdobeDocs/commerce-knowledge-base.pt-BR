---
title: Solução de problemas de Relatórios avançados do Adobe Commerce
description: Problemas avançados de relatórios no Adobe Commerce podem ser resolvidos usando a ferramenta de solução de problemas. Isso inclui relatórios avançados que não mostram dados e erros 404. Clique em cada pergunta para revelar a resposta em cada etapa da solução de problemas.
exl-id: 7ef9870c-b6b6-4144-a5a7-81aa20a1606c
feature: Cache, Support
role: Developer
source-git-commit: 84b4ca4c4144381f0b404d2eae6684e7b21755df
workflow-type: tm+mt
source-wordcount: '983'
ht-degree: 0%

---

# Solução de problemas de Relatórios avançados do Adobe Commerce

Problemas avançados de relatórios no Adobe Commerce podem ser resolvidos usando a ferramenta de solução de problemas. Isso inclui relatórios avançados que não mostram dados e erros 404. Clique em cada pergunta para revelar a resposta em cada etapa da solução de problemas.

## Etapa 1 - Confirmar se o site atende aos Requisitos Avançados de Geração de Relatórios {#step-1}

+++**Seu site atende aos requisitos avançados de relatórios?**

Você tem uma página de Erro 404 ao usar a Geração de relatórios avançada. O seu site atende [Requisitos avançados de relatórios](https://docs.magento.com/user-guide/reports/advanced-reporting.html#requirements)?

a. SIM - Vá para [Etapa 2](#step-2).\
b. NÃO - Preencha os requisitos avançados de relatórios para seu site seguindo as etapas em [Requisitos avançados de relatórios](https://docs.magento.com/user-guide/reports/advanced-reporting.html#requirements). Em seguida, prossiga para [Etapa 2](#step-2).

+++

## Etapa 2 - Há pedidos em várias moedas base? {#step-2}

+++**Várias moedas base são usadas?**

Várias moedas base são usadas (em pedidos e configuração)? Execute este comando SQL para obter a configuração atual: `SELECT value FROM core_config_data WHERE path = 'currency/options/base';` .

a. SIM - Se houver várias linhas retornadas pela consulta, você não poderá usar a Geração de Relatórios Avançados, pois oferecemos suporte a apenas uma moeda.\
b. NÃO - A saída mostra apenas uma moeda. Exemplo: `USD`. Já foram usadas várias moedas base (em pedidos)? Execute este comando SQL para obter dados históricos de pedidos:\
`SELECT DISTINCT base_currency_code FROM sales_order;`.
**OBSERVAÇÃO: Esse comando requer uma varredura integral da tabela, de modo que, para tabelas com altos números de registros, isso pode ter um impacto no desempenho enquanto a consulta está sendo executada** para obter dados históricos de pedidos.
Se várias moedas base tiverem sido usadas, você não poderá usar a Geração de relatórios avançada, pois oferecemos suporte a apenas uma moeda. Se a saída mostrar apenas uma moeda, prossiga para [Etapa 3](#step-3).

+++

## Etapa 3 - Verificar se o banco de dados dividido está em uso {#step-3}

+++**Você está usando a solução de banco de dados dividido?**

Você está usando [dividir solução de banco de dados](https://devdocs.magento.com/guides/v2.3/config-guide/multi-master/multi-master.html)?

a. SIM - Use o patch **MDVA-26831** in [Erro 404 do Advanced Reporting na solução de banco de dados dividido](/help/troubleshooting/known-issues-patches-attached/advanced-reporting-404-error-on-split-database-solution.md) e limpe o cache. Aguarde 24 horas para que o trabalho seja executado novamente e tente novamente.\
b. NÃO - Vá para [Etapa 4](#step-4).

+++

## Etapa 4 - Confirmar relatório avançado habilitado {#step-4}

+++**O Advanced Reporting está habilitado?**

Marcar **Admin** > **Lojas** > **Configurações** > **Configuração** > **Geral** > **Avançado**. Para obter etapas detalhadas, consulte [Relatórios avançados: Ativar relatórios avançados](https://docs.magento.com/user-guide/reports/advanced-reporting.html#step-1-enable-advanced-reporting).

a. SIM - Vá para [Etapa 5](#step-5).\
b. NÃO - [Ativar relatórios avançados](https://docs.magento.com/user-guide/reports/advanced-reporting.html#step-1-enable-advanced-reporting) e salve e aguarde 24 horas para que o Adobe Commerce e o Advanced Reporting sejam sincronizados. Verifique se os dados agora são carregados. Se isso acontecer, você resolveu o problema. Se não proceder a [Etapa 5](#step-5).

+++

## Etapa 5 - Verificar token {#step-5}

+++**Há um token?**

Verifique se há um token executando a seguinte consulta: `SELECT * FROM core_config_data WHERE path LIKE 'analytics/general/token' \G` Há um token?

a. SIM - Vá para [Etapa 7](#step-7).\
b. NÃO - Se o valor do token for NULL ou não houver registro no banco de dados, prossiga para [Etapa 6](#step-6).

+++

## Etapa 6 - Usar a linha {#step-6}

+++**A consulta retorna a linha?**

Verifique o valor do contador na tabela de sinalizadores executando esta consulta: ``SELECT * FROM `flag` where `flag_code` = 'analytics_link_subscription_update_reverse_counter'\G`` A consulta retorna a linha?

a. SIM - Execute as seguintes etapas: 1. Execute a consulta abaixo:\
``DELETE from `flag` where `flag_code` = 'analytics_link_subscription_update_reverse_counter';``\
2\ [Desativar e ativar o módulo de relatórios avançados](https://docs.magento.com/user-guide/reports/advanced-reporting.html#step-1-enable-advanced-reporting) em configurações e [reautorizar o token](https://docs.magento.com/user-guide/reports/advanced-reporting.html#verify-that-the-integration-is-active).\
3 Aguarde 24 horas para que o Adobe Commerce e o Advanced Reporting sincronizem. Se ainda não conseguir ver os dados nos Relatórios avançados, [enviar um tíquete de suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
b. NÃO - Se a consulta não retornar nada, siga estas etapas: 1. [Desativar e ativar o módulo de relatórios avançados](https://docs.magento.com/user-guide/reports/advanced-reporting.html#step-1-enable-advanced-reporting) em configurações e [reautorizar o token](https://docs.magento.com/user-guide/reports/advanced-reporting.html#verify-that-the-integration-is-active).\
2\ Aguarde 24 horas para que o Adobe Commerce e o Advanced Reporting sincronizem. Se ainda não conseguir ver os dados nos Relatórios avançados, [enviar um tíquete de suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

## Etapa 7 - Verificar registros em `cron_schedule` tabela {#step-7}

+++**Há registros na variável `cron_schedule` tabela?**

Verifique esse trabalho `analytics_collect_data` foi executado executando esta consulta: `SELECT * FROM cron_schedule WHERE job_code LIKE 'analytics_collect_data' \G`

a. SIM - Se houver registros e o **status** diz a coluna _ausente_, use o patch neste artigo da KB [Atualizar relatório avançado para executar em seu próprio grupo cron](/help/troubleshooting/known-issues-patches-attached/update-advanced-reporting-to-run-on-its-own-cron-group.md).\
b. SIM - Se houver registros e as **status** diz a coluna _success_, prossiga para [Etapa 9](#step-9).\
c. SIM - Se houver registros e a **status** diz a coluna _erro_, prossiga para [Etapa 8.](#step-8)\
d. NÃO - Se não houver registros, vá para [Etapa 8](#step-8).

+++

## Etapa 8 - Verificar trabalho em `support_report.log` {#step-8}

+++**O trabalho foi conectado? `support_report.log`?**

Execute o comando: `zgrep analytics_collect_data var/log/support_report.log var/log/support_report.log.1.gz | tail`

a. SIM - Se a saída da consulta indicar um job bem-sucedido, por exemplo `Cron Job analytics_collect_data is successfully finished` prosseguir para [Etapa 9](#step-9).\
b. NÃO - Se não houver registros no log, [enviar um tíquete de suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
c. SIM - Se houver registros, mas houver um erro, vá para [Etapa 10](#step-10).

+++

## Etapa 9 - Verificar `data.tgz` arquivo {#step-9}

+++**Faz o arquivo `data.tgz` existe no sistema e há registros nos logs de acesso?**

Para verificar se o arquivo `data.tgz` existe, execute o comando:

```
ls -ltr pub/media/analytics/<there should be a directory with hash name>/
```

Para verificar se há registros em access.logs, execute o comando:

```
zgrep -i analytics /var/log/platform/[cluster_id|cluster_id_stg]/access.log* | grep MagentoBI
```

a. SIM - Se o arquivo `data.tgz` estiver presente e houver registros nos logs de acesso, mas ainda houver um erro 404, é necessário [enviar um tíquete de suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
b. NÃO - Vá para [Etapa 10](#step-10).

+++

## Etapa 10 - Verificar a mensagem de erro {#step-10}

+++**Há uma mensagem de erro emitida pelo trabalho cron?**

Exemplo: na caixa `core_config_data` tabela em que você vê o erro *O arquivo &quot;/app/var/tmp/analytics/tmp/.nfsb3b6041dd44588a0000850c0 não pode ser excluído*. Aviso!unlink(/app/var/tmp/analytics/tmp/.nfsb3b6041dd44588a0000850c0?lang=en): Arquivo ou diretório inexistente*

a. SIM - Use o patch ACSD-50165 no [O arquivo não pode ser excluído. Aviso!unlink: erro de arquivo ou diretório inexistente no Administrador](/help/troubleshooting/miscellaneous/file-cannot-be-deleated-no-file-or-directory.md), aguarde 24 horas para que o trabalho seja executado novamente e tente novamente.\
b. NÃO - Vá para [Etapa 11](#step-11).

+++

## Etapa 11 - Verificar se há um erro do Page Builder {#step-11}

+++**Há um erro causado pelo Page Builder?**

Exemplo: `report.ERROR: Cron Job analytics_collect_data has an error: substr_count() expects parameter 1 to be string, null given. Statistics: {"sum":0,"count":1,"realmem":0,"emalloc":0,"realmem_start":224919552,"emalloc_start":216398384} [] []`

a. SIM - Use o patch MDVA-19391 no [Erros comuns no trabalho cron do Advanced Reporting no Adobe Commerce](/help/troubleshooting/known-issues-patches-attached/advanced-reporting-cron-job-errors-magento-commerce.md), aguarde 24 horas para que o trabalho seja executado novamente e tente novamente.\
b. NÃO - [enviar um tíquete de suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

[Voltar à Etapa 1](#step-1)
