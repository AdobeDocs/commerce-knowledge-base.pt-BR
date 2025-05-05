---
title: O índice está bloqueado por outro processo
description: Este artigo fala sobre um problema comum de indexação no Adobe Commerce, em que o índice é bloqueado por outro processo e ignorado.
exl-id: 542c714c-fad5-4f0e-9757-d90044c36bfc
feature: Catalog Management, Categories
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 0%

---

# O índice está bloqueado por outro processo

Este artigo fala sobre um problema comum de indexação no Adobe Commerce, em que o índice é bloqueado por outro processo e ignorado.

## Produtos e versões afetados

* Adobe Commerce 2.X

## Problema

Durante uma reindexação completa na CLI, o Adobe Commerce fornece a mensagem de erro: o índice *está bloqueado por outro processo de reindexação. Pulando.&#39;* Em outras palavras, quando o processo ou o tipo de índice estiver bloqueado, você não poderá reindexar esse tipo de índice bloqueado específico. O reindexação sempre ignorará esse tipo de índice.

## Causa

Esse erro poderá ocorrer se o índice anterior não for concluído com êxito. Algumas razões possíveis são:

* O processo foi interrompido por outro processo ou usuário.
* Limite de memória.
* Erro de MySQL, como tempo limite.
* Erro fatal do PHP durante a reindexação.

## Etapas a serem reproduzidas

1. Por exemplo, digamos que a variável    ```bash    cataloginventory_stock ```    o tipo de índice está bloqueado.
1. Quando você tenta reindexar todos os dados executando o comando da CLI    ```bash    php bin/magento indexer:reindex    ```, você obterá o seguinte resultado de saída:    ```bash    customer_grid index has been rebuilt successfully in 00:00:09    catalog_category_product index has been rebuilt successfully in 00:00:07    catalog_product_category index has been rebuilt successfully in 00:00:00    catalogrule_rule index has been rebuilt successfully in 00:00:05    catalog_product_attribute index has been rebuilt successfully in 00:00:04    cataloginventory_stock index is locked by another reindex process. Skipping.    catalog_product_price index has been rebuilt successfully in 00:00:01    catalogrule_product has been rebuilt successfully in 00:00:00    catalogsearch_fulltext index has been rebuilt successfully in 00:00:01    ```
1. Como você pode ver acima, a variável    ```bash    cataloginventory_stock```    o processo de indexação foi ignorado.


## Solução

Você precisa redefinir o status do índice e tentar executar o novo processo de reindexação. Para redefinir o status do índice, é necessário executar o comando:

```bash
bin/magento indexer:reset <index identifier>
```

Se não tiver certeza sobre quais são os identificadores de índice (código), é possível listá-los usando o comando:

```bash
bin/magento indexer:info
```

Para fins de integridade, estas são todas as combinações possíveis para índices nativos:

```bash
bin/magento indexer:reset design_config_grid;
bin/magento indexer:reset customer_grid;
bin/magento indexer:reset catalog_category_product;
bin/magento indexer:reset catalog_product_category;
bin/magento indexer:reset catalogrule_rule;
bin/magento indexer:reset catalog_product_attribute;
bin/magento indexer:reset cataloginventory_stock;
bin/magento indexer:reset catalog_product_price;
bin/magento indexer:reset catalogrule_product;
bin/magento indexer:reset catalogsearch_fulltext;
```


## Leitura relacionada

Em nossa base de conhecimento de suporte:

* [As tarefas do Cron bloqueiam tarefas de outros grupos (Adobe Commerce na infraestrutura em nuvem)](/help/troubleshooting/miscellaneous/cron-tasks-lock-tasks-from-other-groups.md)

Em nosso guia do usuário:

* [Gerenciamento de Índice](https://experienceleague.adobe.com/pt-br/docs/commerce-admin/systems/tools/index-management?itm_source=merchdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=reindexing)

Em nossa documentação do desenvolvedor:

* [Visão geral da indexação](https://developer.adobe.com/commerce/php/development/components/indexing/)
* [Práticas recomendadas para indexadores](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/performance-best-practices/configuration)
* [Configurar E Executar O Cron](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs)
* [Gerenciar Os Indexadores](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/configuration-guide/cli/manage-indexers)
* [Otimização do Indexador](https://developer.adobe.com/commerce/php/development/components/indexing/optimization/)
