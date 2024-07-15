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

Este artigo fornece uma solução para erros de conexão de banco de dados no `var/log/exception.log` que podem ocorrer durante a importação de um grande número de produtos ou a execução de outra tarefa que força o servidor a manipular pacotes maiores do que o configurado no `max_allowed_packet`, que é maior do que o padrão, 16MB.

## Produtos e versões afetados

* Adobe Commerce local, todas as [versões com suporte](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Problema

Quando um cliente MySQL ou o servidor [mysqld](https://dev.mysql.com/doc/refman/8.0/en/mysqld.html) recebe um pacote maior que [max\_allowed\_packet](https://dev.mysql.com/doc/refman/8.0/en/server-system-variables.html#sysvar_max_allowed_packet) bytes, ele emite um erro [ER\_NET\_PACKET\_TOO\_LARGE](https://dev.mysql.com/doc/mysql-errors/8.0/en/server-error-reference.html#error_er_net_packet_too_large) (que pode ser visto no `exception.log`) e fecha a conexão. Com alguns clientes, você também pode obter uma conexão *Perdida com o MySQL server durante o erro query* se o pacote de comunicação for muito grande.

<u>Etapas a serem reproduzidas</u>

Várias tarefas podem produzir esse problema. Isso pode incluir tentar importar um grande número de produtos para o Adobe Commerce ou consultas transacionais enviando dados demais. O resultado são erros de conexão de banco de dados em `var/log/exception.log` e outros problemas, como produtos que não foram importados com êxito.

## Causa

O valor padrão de 16MB para a configuração `max_allowed_packets` do MySQL não é grande o suficiente para suas necessidades.

## Solução

1. Identifique consultas nas quais as linhas individuais excedem o limite atual de `max_allowed_packet`. Essas consultas precisam ser regravadas para reduzir a quantidade de dados retornados. Isso pode ser feito tendo um número menor de colunas na instrução `SELECT` ou escolhendo um tipo de dados menor para várias colunas como parte do design da tabela. Se você tiver uma conta do New Relic, use a [página Erros de APM do New Relic](https://docs.newrelic.com/docs/apm/apm-ui-pages/error-analytics/errors-page-explore-events-behind-errors) e a [página Bancos de Dados de APM do New Relic](https://docs.newrelic.com/docs/apm/apm-ui-pages/monitoring/databases-page-view-operations-throughput-response-time) e os [Logs do New Relic](https://docs.newrelic.com/docs/logs/log-management/get-started/get-started-log-management) para procurar as consultas relevantes.
1. Para correção rápida, você pode solicitar temporariamente que o tamanho de `max_allowed_packet` seja aumentado ao [enviar um tíquete](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket), mas isso fica a critério da equipe de engenharia de clientes, pois um valor muito grande pode causar falhas de replicação, causando congestionamento de rede.
1. Como prática recomendada, você deve executar o seguinte comando na CLI para algumas das tabelas grandes do banco de dados:

   ```
   show table status like [table name to match]
   ```

   Avalie as consultas em execução nessas tabelas para determinar se você está excedendo o tamanho `max_allowed_packet` recomendado de 16 MB. Siga o mesmo processo na etapa um para reduzir os dados retornados por essas consultas.

## Leitura relacionada

* [Guia de Instalação > MySQL](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/mysql.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=max%20allowed%2016%20MB) em nossa documentação de desenvolvedor.
* [O carregamento do banco de dados perde a conexão com o MySQL](/help/troubleshooting/database/database-upload-loses-connection-to-mysql.md) em nossa knowledge base de suporte.
* [Práticas recomendadas do banco de dados para Adobe Commerce na infraestrutura em nuvem](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html) em nossa base de dados de conhecimento de suporte.
* [Práticas recomendadas para resolver problemas de desempenho do banco de dados](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/resolve-database-performance-issues.html) em nossa base de dados de conhecimento de suporte.
