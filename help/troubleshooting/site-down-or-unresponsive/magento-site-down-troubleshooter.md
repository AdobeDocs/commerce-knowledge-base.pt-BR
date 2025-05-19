---
title: Solução de problemas de inatividade do site Adobe Commerce
description: Clique em cada pergunta para revelar os detalhes da resposta em cada etapa da solução de problemas.
exl-id: 10a2313e-cc82-4ffc-9247-624884f3e165
feature: Support
role: Developer
source-git-commit: 66ff85507ec91def7aa836469b243c32c4e161cc
workflow-type: tm+mt
source-wordcount: '800'
ht-degree: 0%

---

# Solução de problemas de inatividade do site Adobe Commerce

Clique em cada pergunta para revelar os detalhes da resposta em cada etapa da solução de problemas.

>[!NOTE]
>
>Antes de criar um [Tíquete de Suporte](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide?lang=en#support-cases), verifique a página [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) para ver se seu problema já está listado.

## Etapa 1 {#step-1}

+++**O <https://status.adobe.com> mostra algum problema?**

a. SIM - Se você marcou [Status do Adobe Commerce](https://status.adobe.com/cloud/experience_cloud) e ele apresentou um problema, abra um [Tíquete de Suporte](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-cases) para fazer uma investigação mais aprofundada.\
b. NÃO - Se você verificou o [Status do Adobe Commerce](https://status.adobe.com/cloud/experience_cloud) e ele não apresentou um problema, prossiga para a [Etapa 2](#step-2).

+++

## Etapa 2 {#step-2}

+++**O http://status.fastly.com mostra algum problema?**

a. SIM - Se você marcou [[!DNL Fastly] Status](https://status.fastly.com/) e ele mostrou um problema, abra um [Tíquete de Suporte](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-cases) para fazer uma investigação mais aprofundada.\
b. NÃO - Se você verificou o [[!DNL Fastly] Status](https://status.fastly.com/) e ele não apresentou um problema, prossiga para a [Etapa 3](#step-3).

+++

## Etapa 3 {#step-3}

+++**Verifique o site em um navegador da Web. Você recebeu um código 200 (OK)?**

Para verificar códigos de erro no **Firefox**: clique no ícone **Abrir Menu** > **Desenvolvedor da Web** > **Alternar Ferramentas** > guia **Rede** > **Filtro de todos os** > coluna **Status**. Para verificar códigos de erro no **Chrome**: clique no ícone **Abrir Menu** > **Mais Ferramentas** > **Ferramentas do Desenvolvedor** > guia **Rede** > **Todos** filtro > **Status** coluna.

a. SIM - Abra um [Tíquete de Suporte](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-cases) para fazer uma investigação mais detalhada.\
b. NÃO - Continue na [Etapa 4](#step-4).

+++

## Etapa 4 {#step-4}

+++**Que código de erro de site você recebeu?**

a. Código de erro 500 - Verifique o log de `/var/log/platform/`. Se esses dados não apresentarem o problema para você, abra um [Tíquete de Suporte](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-cases) e inclua as informações de solução de problemas que você tem até agora para fazer uma investigação mais aprofundada.

b. Código de erro 503 - Verifique o log de `var/reports`. Se esses dados não apresentarem o problema para você, abra um [Tíquete de Suporte](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-cases) e inclua as informações de solução de problemas que você tem até agora para fazer uma investigação mais aprofundada.

c. Código de erro 404 - Execute a seguinte consulta: `SELECT f.flag_data->>'$.current_version' as flag_version, (su.id IS NOT NULL) as update_exists FROM flag f LEFT JOIN staging_update su ON su.id = f.flag_data->>'$.current_version' WHERE flag_code = 'staging';` Se a consulta retornar uma tabela, onde o valor `update_exists` é &quot;0&quot;, consulte o artigo [Erro 404 em todas as páginas, vitrine e administração, devido ao problema de Preparo de Conteúdo](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/troubleshooting/site-down-or-unresponsive/error-404-on-all-pages-due-to-content-staging-issue). Em todos os outros casos, prossiga para a [Etapa 5](#step-5).

d. Outros códigos de erro - Continue na [Etapa 5](#step-5).

+++

## Etapa 5 {#step-5}

+++**Seu site está lento ou com alta carga do servidor, alta carga do CPU, processamento lento de solicitações ou interrupções no [!DNL MySQL] ou no Redis?**

a. SIM - Continue com as etapas para [Verificação de ataques de DDOS da CLI](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/checking-for-ddos-attack-from-cli).\
b. NÃO - Verifique os logs de `/var/log/exception.log` e `/var/log/deploy.log`. Se esses dados não apresentarem o problema a você, prossiga para a [Etapa 6](#step-6).

+++

## Etapa 6 {#step-6}

+++**Você tem erros de implantação ou falha de implantação?**

a. SIM - Continue na [Etapa 13](#step-13).\
b. NÃO - Continue na [Etapa 7](#step-7).

+++

## Etapa 7 {#step-7}

+++**Você tem erros de Elasticsearch?**

a. SIM - Continue com as etapas para [verificar o Elasticsearch](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/configuration-guide/search/configure-search-engine).
b. NÃO - Continue na [Etapa 8](#step-8).

+++

## Etapa 8 {#step-8}

+++**Seu banco de dados [!DNL MySQL] estava com consultas lentas ou incorretas?**

a. SIM - Continue com [Verificando consultas lentas e Processos demorando muito em [!DNL MySQL]](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/troubleshooting/database/checking-slow-queries-and-processes-mysql) and checking your query structure in this [[!DNL MySQL] tutorial de consulta](https://dev.mysql.com/doc/refman/5.5/en/entering-queries.html).\
b. NÃO - Continue na [Etapa 9](#step-9).

+++

## Etapa 9 {#step-9}

+++**Seu conteúdo estático não está disponível?**

a. SIM - Continue consultando o artigo [Verificação de conteúdo estático](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/implementation-playbook/best-practices/development/static-content-deployment).\
b. NÃO - Continue na [Etapa 10](#step-10).

+++

## Etapa 10 {#step-10}

+++**Você vê erros fatais do PHP em seus logs?**

a. SIM - Continue com a consultoria [Erros Fatais Comuns do PHP e soluções](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/common-php-fatal-errors-and-solutions).\
b. NÃO - Continue na [Etapa 11](#step-11).

+++

## Etapa 11 {#step-11}

+++**Você está vendo erros de Redis?**

a. SIM - Continue com as etapas para [verificar [!DNL Redis] está em execução](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/configuration-guide/cache/redis/redis-session#verify-redis-connection) e para [[!DNL Redis] solução de problemas](https://redis.io/topics/problems).\
b. NÃO - Continue na [Etapa 12](#step-12).

+++

## Etapa 12 {#step-12}

+++**Você está vendo erros de Indexador?**

a. SIM - Se o índice estiver bloqueado por outro processo, consulte [O índice está bloqueado por outro processo](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/index-is-locked-by-another-process). Se você tiver outros erros de Indexador, abra um [Tíquete de Suporte](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-cases) para fazer uma investigação mais aprofundada.\
b. NÃO - Abra um [Tíquete de Suporte](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-cases) para investigação adicional.

+++

## Etapa 13 {#step-13}

+++**Você tem problemas com seu(s) módulo(s) personalizado(s)?**

a. SIM - Continue consultando a [ajuda geral para a solução de problemas do módulo personalizado](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/general-custom-module-troubleshooting-help).\
b. NÃO - Continue na [Etapa 14](#step-14).

+++

## Etapa 14 {#step-14}

+++**Você tem falhas de pós-gancho?**

a. SIM - Continue verificando o erro do [!DNL MySQL] nesta [[!DNL MySQL] referência da mensagem de erro do servidor](https://dev.mysql.com/doc/mysql-errors/5.7/en/server-error-reference.html).\
b. NÃO - Continue na [Etapa 15](#step-15).

+++

## Etapa 15 {#step-15}

+++**Você tem problemas com os patches do compositor?**

a. SIM - Prossiga para a consultoria [A aplicação de uma correção desativa seu site](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/troubleshooting/site-down-or-unresponsive/applying-a-patch-takes-your-site-down).\
b. NÃO - Continue na [Etapa 16](#step-16).

+++

## Etapa 16 {#step-16}

+++**Você tem erros de banco de dados SQL?**

a. SIM - Continue verificando o erro do [!DNL MySQL] nesta [[!DNL MySQL] referência da mensagem de erro do servidor](https://dev.mysql.com/doc/mysql-errors/5.7/en/server-error-reference.html).\
b. NÃO - Continue na [Etapa 17](#step-17).

+++

## Etapa 17 {#step-17}

+++**Você tem [!DNL MySQL] bloqueios inativos do banco de dados ou um banco de dados [!DNL MySQL] sem resposta?**

a. SIM - Continue verificando se há [!DNL MySQL] deadlocks neste [Artigo de  [!DNL MySQL]](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/troubleshooting/database/deadlocks-in-mysql).\
b. NÃO - Abra um [Tíquete de Suporte](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-cases) para investigação adicional.

+++

[Voltar à Etapa 1](#step-1)

Clique [AQUI](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/troubleshooting/site-down-or-unresponsive/site-down-troubleshooting-diagram) para ver o Fluxograma de Solução de Problemas de Site Inativo.

## Leitura relacionada

[Práticas recomendadas para modificar tabelas de banco de dados](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) no Manual de implementação do Commerce
