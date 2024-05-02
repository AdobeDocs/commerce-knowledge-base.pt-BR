---
title: Erros de banco de dados relacionados a max_allowed_packet no Adobe Commerce
description: Este artigo fornece uma solução para erros de conexão de banco de dados no "var/log/exception.log" que podem ocorrer ao importar um grande número de produtos ou executar outra tarefa que força o servidor a lidar com pacotes maiores do que o definido em "max_allowed_packet", que é maior do que o padrão, 16MB.
exl-id: e8932b72-91a3-43ea-800e-a6c7a5a17656
feature: Best Practices, Observability, Services
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 0%

---

# Erros de banco de dados relacionados a max_allowed_packet no Adobe Commerce

Este artigo fornece uma solução para erros de conexão de banco de dados no `var/log/exception.log` que podem ocorrer ao importar um grande número de produtos ou executar outra tarefa que força o servidor a lidar com pacotes maiores do que os definidos no `max_allowed_packet` maior que o padrão, 16MB.

## Produtos e versões afetados

* Adobe Commerce no local, tudo [versões compatíveis](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Problema

Quando um cliente MySQL ou o [mysqld](https://dev.mysql.com/doc/refman/8.0/en/mysqld.html) o servidor recebe um pacote maior que [max\_allowed\_packet](https://dev.mysql.com/doc/refman/8.0/en/server-system-variables.html#sysvar_max_allowed_packet) bytes, ele emite um comando [ER\_NET\_PACKET\_TOO\_LARGE](https://dev.mysql.com/doc/mysql-errors/8.0/en/server-error-reference.html#error_er_net_packet_too_large) erro (que pode ser visto na variável `exception.log`) e fecha a conexão. Com alguns clientes, você também pode obter uma *Conexão com o servidor MySQL perdida durante a consulta* erro se o pacote de comunicação for muito grande.

<u>Etapas a serem reproduzidas</u>

Várias tarefas podem produzir esse problema. Isso pode incluir tentar importar um grande número de produtos para o Adobe Commerce ou consultas transacionais enviando dados demais. O resultado são erros de conexão de banco de dados em `var/log/exception.log` e outros problemas, como produtos que não foram importados com êxito.

## Causa

O valor padrão de 16 MB para o MySQL `max_allowed_packets` A configuração do não é grande o suficiente para atender às suas necessidades.

## Solução

1. Identificar consultas em que as linhas individuais excedem o valor atual `max_allowed_packet` limite. Essas consultas precisam ser regravadas para reduzir a quantidade de dados retornados. Isso pode ser feito com um número menor de colunas no `SELECT` ou escolher um tipo de dados menor para várias colunas como parte do design da tabela. Se você tiver uma conta do New Relic, use o [Página Erros de APM do New Relic](https://docs.newrelic.com/docs/apm/apm-ui-pages/error-analytics/errors-page-explore-events-behind-errors) e a variável [Página Bancos de Dados APM do New Relic](https://docs.newrelic.com/docs/apm/apm-ui-pages/monitoring/databases-page-view-operations-throughput-response-time), e [Logs do New Relic](https://docs.newrelic.com/docs/logs/log-management/get-started/get-started-log-management) para procurar as consultas relevantes.
1. Para uma correção rápida, você pode solicitar temporariamente a `max_allowed_packet` tamanho a ser aumentado quando você [enviar um tíquete](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket), mas isso fica a critério da equipe de engenharia do cliente, pois um valor muito grande pode causar falhas de replicação, causando congestionamento de rede.
1. Como prática recomendada, você deve executar o seguinte comando na CLI para algumas das tabelas grandes do banco de dados:

   ```
   show table status like [table name to match]
   ```

   Avalie as consultas executadas nessas tabelas para determinar se você está excedendo o recomendado `max_allowed_packet` tamanho de 16 MB. Siga o mesmo processo na etapa um para reduzir os dados retornados por essas consultas.

## Leitura relacionada

* [Guia de instalação > MySQL](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/mysql.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=max%20allowed%2016%20MB) na documentação do desenvolvedor.
* [O upload do banco de dados perde a conexão com o MySQL](/help/troubleshooting/database/database-upload-loses-connection-to-mysql.md) em nossa base de conhecimento de suporte.
* [Práticas recomendadas de banco de dados para o Adobe Commerce na infraestrutura em nuvem](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html) em nossa base de conhecimento de suporte.
* [Práticas recomendadas para resolver problemas de desempenho do banco de dados](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/resolve-database-performance-issues.html) em nossa base de conhecimento de suporte.
