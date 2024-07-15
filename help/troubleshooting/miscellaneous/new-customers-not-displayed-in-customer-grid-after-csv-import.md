---
title: Novos clientes não são exibidos na grade Cliente após a importação do CSV
description: Este artigo fornece uma correção para o problema que ocorre quando não é possível ver novos clientes em **Customers** &gt; **All customers** após uma importação de um arquivo `.csv`. A solução é definir o indexador `customer_grid` para o modo "Atualizar ao salvar" e reindexar manualmente a grade do cliente.
exl-id: e4d9d60a-a0d1-4602-924e-a338e56de61d
feature: Data Import/Export
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '288'
ht-degree: 0%

---

# Novos clientes não são exibidos na grade Cliente após a importação do CSV

Este artigo fornece uma correção para o problema que ocorre quando não é possível ver novos clientes em **Clientes** > **Todos os clientes** após uma importação de um arquivo `.csv`. A solução é definir o indexador `customer_grid` para o modo &quot;Atualizar ao Salvar&quot; e reindexar manualmente a grade do cliente.

## Versões afetadas

* Adobe Commerce no local 2.2.0 e posterior
* Adobe Commerce na infraestrutura em nuvem 2.2.0 e posterior

## Problema

Depois de importar novos clientes de um arquivo `.csv` usando a funcionalidade de importação nativa do Adobe Commerce, talvez você não possa ver os novos registros de clientes em **Clientes** > **Todos os clientes** no Administrador até reindexar manualmente o indexador `customer_grid`.

## Causa

O modo de indexação &quot;Atualização na Programação&quot; no Adobe Commerce 2.2.0 e posterior não oferece suporte ao indexador `customer_grid` devido a problemas de desempenho.

## Solução

Configure o indexador `customer_grid` para ser reindexado usando o modo &quot;Atualizar ao Salvar&quot;. Para fazer isso, siga estas etapas:

1. Faça logon no Administrador do Commerce.
1. Clique em **Sistema** > **Ferramentas** > **Gerenciamento de Índice**.
1. Marque a caixa de seleção ao lado do Indexador de grade do cliente.
1. Na lista suspensa **Ações**, selecione *Atualizar ao Salvar*.
1. Clique em **Enviar**.

Também recomendamos reindexar manualmente o indexador `customer_grid` após configurar o modo de indexação para garantir que o índice esteja atualizado e possa funcionar com o cron. Para reindexar manualmente, use o seguinte comando:

`bin/magento indexer:reindex customer_grid`

## Mais informações

Links para tópicos relacionados na documentação do desenvolvedor:

* [Visão geral da indexação](https://devdocs.magento.com/guides/v2.3/extension-dev-guide/indexing.html)
* [Gerenciar os indexadores](https://devdocs.magento.com/guides/v2.3/config-guide/cli/config-cli-subcommands-index.html)
