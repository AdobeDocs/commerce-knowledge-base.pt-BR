---
title: Solução de problemas de Relatórios avançados do Adobe Commerce
description: Problemas avançados de relatórios no Adobe Commerce podem ser resolvidos usando a ferramenta de solução de problemas. Isso inclui relatórios avançados que não mostram dados e erros 404. Clique em cada pergunta para revelar a resposta em cada etapa da solução de problemas.
exl-id: 7ef9870c-b6b6-4144-a5a7-81aa20a1606c
feature: Cache, Support
role: Developer
source-git-commit: 50262a7b98091d4388668c984cfd8237bd534bad
workflow-type: tm+mt
source-wordcount: '1035'
ht-degree: 0%

---

# Solução de problemas de Relatórios avançados do Adobe Commerce

Problemas avançados de relatórios no Adobe Commerce podem ser resolvidos usando a ferramenta de solução de problemas. Isso inclui relatórios avançados que não mostram dados e erros 404. Clique em cada pergunta para revelar a resposta em cada etapa da solução de problemas.

## Etapa 1 - Confirmar se o site atende aos Requisitos Avançados de Geração de Relatórios {#step-1}

+++**Seu site atende aos Requisitos Avançados de Relatório?**

Você tem uma página de Erro 404 ao usar a Geração de relatórios avançada. Seu site atende aos [Requisitos Avançados de Relatório](https://experienceleague.adobe.com/en/docs/commerce-admin/start/reporting/business-intelligence#advanced-reporting#requirements)?

a. SIM - Continue na [Etapa 2](#step-2).\
b. NÃO - Complete os requisitos avançados de relatórios para o site seguindo as etapas dos [requisitos avançados de relatórios](https://experienceleague.adobe.com/en/docs/commerce-admin/start/reporting/business-intelligence#advanced-reporting#requirements). Em seguida, prossiga para [Etapa 2](#step-2).

+++

## Etapa 2 - Há pedidos em várias moedas base? {#step-2}

+++**Várias moedas base estão sendo usadas?**

Várias moedas base são usadas (em pedidos e configuração)? Execute este comando [!DNL SQL] para obter a configuração atual: `SELECT value FROM core_config_data WHERE path = 'currency/options/base';` .

a. SIM - Se houver várias linhas retornadas pela consulta, você não poderá usar **[!UICONTROL Advanced Reporting]**, pois oferecemos suporte a apenas uma moeda. Você terá que usar o [Adobe Commerce Intelligence](https://experienceleague.adobe.com/en/docs/commerce-business-intelligence/mbi/guide-overview). Entre em contato com a equipe de conta para configurar isso.
b. NÃO - A saída mostra apenas uma moeda. Exemplo: `USD`. Já foram usadas várias moedas base (em pedidos)? Execute este comando [!DNL SQL] para obter dados históricos de pedidos:\
`SELECT DISTINCT base_currency_code FROM sales_order;`.
**OBSERVAÇÃO: este comando requer uma verificação completa da tabela; portanto, para tabelas com altos números de registros, isso pode ter um impacto no desempenho enquanto a consulta está sendo executada** para obter dados históricos de pedidos.
Se várias moedas base tiverem sido usadas, você não poderá usar a Geração de relatórios avançada, pois oferecemos suporte a apenas uma moeda. Se a saída mostrar apenas uma moeda, prossiga para [Etapa 3](#step-3).

+++

## Etapa 3 - Verificar se o banco de dados dividido está em uso {#step-3}

+++**Você está usando a solução de banco de dados dividido?**

Você está usando a [solução de banco de dados dividido](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/storage/split-db/multi-master)?

a. SIM - Use o patch **MDVA-26831** no erro 404 do Advanced Reporting na solução de banco de dados dividido e limpar cache. Aguarde 24 horas para que o trabalho seja executado novamente e tente novamente.\
b. NÃO - Continue na [Etapa 4](#step-4).

+++

## Etapa 4 - Confirmar relatório avançado habilitado {#step-4}

+++**Os Relatórios Avançados estão habilitados?**

Verificar **Administrador** > **Lojas** > **Configurações** > **Configuração** > **Geral** > **Relatórios Avançados**. Para obter etapas detalhadas, consulte [Relatórios avançados: Habilitar relatórios avançados](https://experienceleague.adobe.com/en/docs/commerce-admin/start/reporting/business-intelligence#advanced-reporting#step-1-enable-advanced-reporting).

a. SIM - Continue na [Etapa 5](#step-5).\
b. NÃO - [Habilite os Relatórios Avançados](https://experienceleague.adobe.com/en/docs/commerce-admin/start/reporting/business-intelligence#advanced-reporting#step-1-enable-advanced-reporting), salve e aguarde 24 horas para que o Adobe Commerce e os Relatórios Avançados sincronizem. Verifique se os dados agora são carregados. Se isso acontecer, você resolveu o problema. Se não prosseguir para [Etapa 5](#step-5).

+++

## Etapa 5 - Verificar token {#step-5}

+++**Há um token?**

Verifique se há um token executando a seguinte consulta: `SELECT * FROM core_config_data WHERE path LIKE 'analytics/general/token' \G` Existe um token?

a. SIM - Continue na [Etapa 7](#step-7).\
b. NO - Se o valor do token for NULL ou não houver registro no banco de dados, prossiga para a [Etapa 6](#step-6).

+++

## Etapa 6 - Usar a linha {#step-6}

+++**A consulta retorna a linha?**

Verifique o valor do contador na tabela de sinalizador executando esta consulta: ``SELECT * FROM `flag` where `flag_code` = 'analytics_link_subscription_update_reverse_counter'\G`` A consulta retorna a linha?

a. SIM - Execute as seguintes etapas: 1. Execute a consulta abaixo:\
``DELETE from `flag` where `flag_code` = 'analytics_link_subscription_update_reverse_counter';``\
2\ [Desabilite e habilite o módulo de Relatórios Avançados](https://experienceleague.adobe.com/en/docs/commerce-admin/start/reporting/business-intelligence#advanced-reporting#step-1-enable-advanced-reporting) nas configurações e [reautorize o token](https://experienceleague.adobe.com/en/docs/commerce-admin/start/reporting/business-intelligence#advanced-reporting#verify-that-the-integration-is-active).\
3 Aguarde 24 horas para que o Adobe Commerce e o Advanced Reporting sincronizem. Se você ainda não conseguir ver os dados nos Relatórios Avançados, [envie um tíquete de suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
b. NÃO - Se a consulta não retornar nada, siga estas etapas: 1. [Desabilite e habilite o módulo de Relatórios Avançados](https://experienceleague.adobe.com/en/docs/commerce-admin/start/reporting/business-intelligence#advanced-reporting#step-1-enable-advanced-reporting) nas configurações e [reautorize o token](https://experienceleague.adobe.com/en/docs/commerce-admin/start/reporting/business-intelligence#advanced-reporting#verify-that-the-integration-is-active).\
2\ Aguarde 24 horas para que o Adobe Commerce e o Advanced Reporting sincronizem. Se você ainda não conseguir ver os dados nos Relatórios Avançados, [envie um tíquete de suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

## Etapa 7 - Verificar registros na tabela `cron_schedule` {#step-7}

+++**Há registros na tabela `cron_schedule`?**

Verifique se o trabalho `analytics_collect_data` foi executado executando esta consulta: `SELECT * FROM cron_schedule WHERE job_code LIKE 'analytics_collect_data' \G`

a. SIM - Se houver registros e a coluna **status** indicar _perdido_, use o patch neste artigo da Base de Dados de Conhecimento em Atualizar Relatórios Avançados para executar em seu próprio grupo cron.\
b. SIM - Se houver registros e a coluna **status** indicar _sucesso_, continue para a [Etapa 9](#step-9).\
c. SIM - Se houver registros e a coluna **status** informar _erro_, prosseguir para a [Etapa 8.](#step-8)\
d. NÃO - Se não houver registros, prossiga para [Etapa 8](#step-8).

+++

## Etapa 8 - Verificar trabalho em `support_report.log` {#step-8}

+++**O trabalho foi conectado em `support_report.log`?**

Execute o comando: `zgrep analytics_collect_data var/log/support_report.log var/log/support_report.log.1.gz | tail`

a. SIM - Se a saída da consulta indicar um trabalho bem-sucedido, por exemplo `Cron Job analytics_collect_data is successfully finished`, prossiga para a [Etapa 9](#step-9).\
b. NÃO - Se não houver registros no log, [envie um tíquete de suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
c. SIM - Se houver registros, mas houver um erro, prossiga para a [Etapa 10](#step-10).

+++

## Etapa 9 - Verificar arquivo `data.tgz` {#step-9}

+++**O arquivo `data.tgz` existe no sistema e há registros nos logs de acesso?**

Para verificar se o arquivo `data.tgz` existe, execute este comando; ele deve retornar diretório(s) com nome(s) de hash:

```
ls -ltr pub/media/analytics/
```

Para verificar se há registros em access.logs, execute este comando:

* No Commerce Cloud:

  ```
  {{zgrep -i analytics /var/log/platform/*/access.log* | grep MagentoBI}}
  ```

* No local, substitua o caminho do arquivo de acordo:
  `zgrep -i analytics <your web server's log path>/access.log* | grep MagentoBI`

a. SIM - Se o arquivo `data.tgz` estiver presente e houver registros nos logs de acesso, mas ainda houver um erro 404, será necessário [enviar um tíquete de suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
b. NÃO - Continue na [Etapa 10](#step-10).

+++

## Etapa 10 - Verificar a mensagem de erro {#step-10}

+++**Há uma mensagem de erro emitida pelo trabalho cron?**

Exemplo: na tabela `cron_schedule`, você vê o erro *O arquivo &quot;/app/var/tmp/analytics/tmp/.nfsb3b6041dd44588a0000850c0 não pode ser excluído*. Aviso!unlink(/app/var/tmp/analytics/tmp/.nfsb3b6041dd44588a0000850c0?lang=en): Arquivo ou diretório inexistente*

a. SIM - Use o patch ACSD-50165 em [O arquivo não pode ser excluído. Aviso!unlink: erro de arquivo ou diretório inexistente no Admin](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26887), aguarde 24 horas para que o trabalho seja executado novamente e tente novamente.\
b. NÃO - Continue na [Etapa 11](#step-11).

+++

## Etapa 11 - Verificar se há um erro do Page Builder {#step-11}

+++**Há um erro causado pelo Page Builder?**

Exemplo: `report.ERROR: Cron Job analytics_collect_data has an error: substr_count() expects parameter 1 to be string, null given. Statistics: {"sum":0,"count":1,"realmem":0,"emalloc":0,"realmem_start":224919552,"emalloc_start":216398384} [] []`

a. SIM - Use o patch MDVA-19391 em erros de job cron do Relatório avançado comum no Adobe Commerce, aguarde 24 horas para que o job seja executado novamente e tente novamente.\
b. NÃO - [enviar um tíquete de suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

[Voltar à Etapa 1](#step-1)

## Leitura relacionada

[Práticas recomendadas para modificar tabelas de banco de dados](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) no Manual de implementação do Commerce
