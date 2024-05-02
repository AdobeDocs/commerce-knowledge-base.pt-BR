---
title: Solução de problemas de inatividade do site Adobe Commerce
description: Clique em cada pergunta para revelar os detalhes da resposta em cada etapa da solução de problemas.
exl-id: 10a2313e-cc82-4ffc-9247-624884f3e165
feature: Support
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '772'
ht-degree: 0%

---

# Solução de problemas de inatividade do site Adobe Commerce

Clique em cada pergunta para revelar os detalhes da resposta em cada etapa da solução de problemas.

## Etapa 1 {#step-1}

+++**Faz <https://status.adobe.com> mostrar algum problema?**

a. SIM - Se você marcou [Status do Magento Adobe](https://status.adobe.com/products/3350) e mostrou um problema, abra um [Tíquete de suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) para uma investigação mais aprofundada.\
b. NÃO - Se você marcou [Status do Magento Adobe](https://status.adobe.com/products/3350) e não tiver mostrado um problema, prossiga para [Etapa 2](#step-2).

+++

## Etapa 2 {#step-2}

+++**O http://status.fastly.com mostra algum problema?**

a. SIM - Se você marcou [Status do Fastly](https://status.fastly.com/) e mostrou um problema, abra um [Tíquete de suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) para uma investigação mais aprofundada.\
b. NÃO - Se você marcou [Status do Fastly](https://status.fastly.com/) e não tiver mostrado um problema, prossiga para [Etapa 3](#step-3).

+++

## Etapa 3 {#step-3}

+++**Verifique seu site em um navegador da Web. Você recebe um código 200 (OK)?**

Para verificar códigos de erro no **Firefox**: Clique no botão **Abrir Menu** ícone > **Desenvolvedor da Web** > **Alternar ferramentas** > **Rede** guia > **Todos** filtro > **Status** coluna. Para verificar códigos de erro no **Cromo**: Clique no botão **Abrir Menu** ícone > **Mais ferramentas** > **Ferramentas do desenvolvedor** > **Rede** guia > **Todos** filtro > **Status** coluna.

a. SIM - Abrir um [Tíquete de suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) para uma investigação mais aprofundada.\
b. NÃO - Vá para [Etapa 4](#step-4).

+++

## Etapa 4 {#step-4}

+++**Que código de erro de site você recebeu?**

a. Código de erro 500 - Verifique o log de `/var/log/platform/`. Se esses dados não apresentarem o problema, você poderá abrir um [Tíquete de suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) e inclua as informações de solução de problemas que você tem até agora para uma investigação mais aprofundada.

b. Código de erro 503 - Verifique o log de `var/reports`. Se esses dados não apresentarem o problema, você poderá abrir um [Tíquete de suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) e inclua as informações de solução de problemas que você tem até agora para uma investigação mais aprofundada.

c. Código de erro 404 - Execute a seguinte consulta: `SELECT f.flag_data->>'$.current_version' as flag_version, (su.id IS NOT NULL) as update_exists FROM flag f LEFT JOIN staging_update su ON su.id = f.flag_data->>'$.current_version' WHERE flag_code = 'staging';` Se a consulta retornar uma tabela, onde `update_exists` é &quot;0&quot;, consulte a [Erro 404 em todas as páginas, vitrine e administração, devido ao problema do preparo de conteúdo](/help/troubleshooting/site-down-or-unresponsive/error-404-on-all-pages-due-to-content-staging-issue.md) artigo. Em todos os outros casos, [Etapa 5](#step-5).

d. Outros códigos de erro - Continue para [Etapa 5](#step-5).

+++

## Etapa 5 {#step-5}

+++**Seu site está lento ou com alta carga do servidor, alta carga de CPU, processamento lento de solicitações ou paralisações no MySQL ou Redis?**

a. SIM - Continue com as etapas para [Verificação de ataques de DDOS a partir da CLI](/help/troubleshooting/miscellaneous/checking-for-ddos-attack-from-cli.md).\
b. NÃO - Verifique os registros de `/var/log/exception.log` e `/var/log/deploy.log`e se esses dados não apresentarem o problema, prossiga para [Etapa 6](#step-6).

+++

## Etapa 6 {#step-6}

+++**Você tem erros de implantação ou falha de implantação?**

a. SIM - Vá para [Etapa 13](#step-13).\
b. NÃO - Vá para [Etapa 7](#step-7).

+++

## Etapa 7 {#step-7}

+++**Você tem erros de Elasticsearch?**

a. SIM - Continue com as etapas para [Elasticsearch de verificação](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/configure-magento.html).\
b. NÃO - Vá para [Etapa 8](#step-8).

+++

## Etapa 8 {#step-8}

+++**Seu banco de dados MySQL estava com consultas lentas ou incorretas?**

a. SIM - Continue com [Verificação de consultas lentas e Processos que demoram muito no MySQL](/help/troubleshooting/database/checking-slow-queries-and-processes-mysql.md) e verificar sua estrutura de consulta nesta [Tutorial de consulta MySQL](https://dev.mysql.com/doc/refman/5.5/en/entering-queries.html).\
b. NÃO - Vá para [Etapa 9](#step-9).

+++

## Etapa 9 {#step-9}

+++**Seu conteúdo estático não está disponível?**

a. SIM - Continue consultando o [Verificação de conteúdo estático](https://support.magento.com/hc/en-us/articles/360031624091) artigo.\
b. NÃO - Vá para [Etapa 10](#step-10).

+++

## Etapa 10 {#step-10}

+++**Você vê erros fatais do PHP em seus registros?**

a. SIM - Continue com a consultoria [Erros fatais comuns do PHP e suas soluções](/help/troubleshooting/miscellaneous/common-php-fatal-errors-and-solutions.md).\
b. NÃO - Vá para [Etapa 11](#step-11).

+++

## Etapa 11 {#step-11}

+++**Você está vendo os erros de Redis?**

a. SIM - Continue com as etapas para [verifique se o Redis está em execução](https://devdocs.magento.com/guides/v2.3/config-guide/redis/redis-session.html#redis-verify) e para [Solução de problemas do Redis](https://redis.io/topics/problems).\
b. NÃO - Vá para [Etapa 12](#step-12).

+++

## Etapa 12 {#step-12}

+++**Você está vendo erros de Indexador?**

a. SIM - Se o índice estiver bloqueado por outro processo, consulte [O índice está bloqueado por outro processo](/help/troubleshooting/miscellaneous/index-is-locked-by-another-process.md). Se você tiver outros erros do Indexador, abra um [Tíquete de suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) para uma investigação mais aprofundada.\
b. NÃO - Abrir um [Tíquete de suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) para uma investigação mais aprofundada.

+++

## Etapa 13 {#step-13}

+++**Você tem problemas com seu(s) módulo(s) personalizado(s)?**

a. SIM - Proceder à consulta [Ajuda geral para a solução de problemas do módulo personalizado](/help/troubleshooting/miscellaneous/general-custom-module-troubleshooting-help.md).\
b. NÃO - Vá para [Etapa 14](#step-14).

+++

## Etapa 14 {#step-14}

+++**Você tem falhas pós-gancho?**

a. SIM - Continue verificando o erro do MySQL nesta [Referência de mensagem de erro do servidor MySQL](https://dev.mysql.com/doc/mysql-errors/5.7/en/server-error-reference.html).\
b. NÃO - Vá para [Etapa 15](#step-15).

+++

## Etapa 15 {#step-15}

+++**Você tem problemas com patches do compositor?**

a. SIM - Continue com a consultoria [A aplicação de um patch derruba o site](/help/troubleshooting/site-down-or-unresponsive/applying-a-patch-takes-your-site-down.md).\
b. NÃO - Vá para [Etapa 16](#step-16).

+++

## Etapa 16 {#step-16}

+++**Você tem erros de banco de dados SQL?**

a. SIM - Continue verificando o erro do MySQL nesta [Referência de mensagem de erro do servidor MySQL](https://dev.mysql.com/doc/mysql-errors/5.7/en/server-error-reference.html).\
b. NÃO - Vá para [Etapa 17](#step-17).

+++

## Etapa 17 {#step-17}

+++**Você tem bloqueios inativos do banco de dados MySQL ou um banco de dados MySQL sem resposta?**

a. SIM - Continue verificando se há bloqueios inativos do MySQL neste [Deadlocks no MySQL](/help/troubleshooting/database/deadlocks-in-mysql.md) artigo.\
b. NÃO - Abrir um [Tíquete de suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) para uma investigação mais aprofundada.

+++

[Voltar à Etapa 1](#step-1)

Clique em [AQUI](/help/troubleshooting/site-down-or-unresponsive/site-down-troubleshooting-diagram.md) para ver o Fluxograma de Troubleshooting de Site Down.
