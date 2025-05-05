---
title: Correção de dados não atualizados nos  [!DNL Commerce Data Exporter] feeds e [!DNL cron] logs de erro com a tabela changelog não existem
description: Este artigo fornece uma solução para corrigir problemas de sincronização de dados causados pelo uso de uma ID de exibição incorreta na assinatura do  [!DNL Commerce Data Exporter mview] .
feature: Data Import/Export, Saas, Logs
role: Developer
exl-id: 50f2223b-bfcf-4c3c-b0f1-dbcc4365edc2
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '261'
ht-degree: 0%

---

# Os dados de correção não foram atualizados nos feeds [!DNL Commerce Data Exporter] e os erros de log [!DNL cron] com a tabela changelog não existem

Este artigo fornece uma solução para corrigir problemas de sincronização de dados causados pelo uso da ID de exibição incorreta na assinatura [!DNL Data Exporter] [[!DNL Mview]](https://developer.adobe.com/commerce/php/development/components/indexing/#mview). A assinatura [!DNL Mview] é usada para rastrear alterações em tabelas de banco de dados.

## Produtos e versões afetados

Instâncias do Adobe Commerce em que o código personalizado foi aplicado à funcionalidade de exportação de dados (`commerce-data-exporter` ou `saas-exporter`). O erro ocorre se a versão instalada do [[!DNL SaaS] Data Export for 103.3.0](https://experienceleague.adobe.com/pt-br/docs/commerce-merchant-services/saas-data-export/release-notes#release-6) ou posterior e o código fizer referência direta ao índice `catalog_data_exporter_products`.

## Problema

Os comerciantes podem descobrir que as atualizações de dados estão ausentes nas tabelas de feed do Catálogo [!DNL Data Exporter] e ver os seguintes erros nos logs de trabalho [!DNL cron]:

```
[2024-05-27T19:00:04.627604+00:00] report.ERROR: Cron Job indexer_clean_all_changelogs has an error: Table catalog_data_exporter_products_cl does not exist. Statistics: {"sum":0,"count":1,"realmem":0,"emalloc":0,"realmem_start":305135616,"emalloc_start":283210384} [] [] 
```

## Causa

Devido a alterações de nome em tabelas de feed, índices e tabelas de log de alterações na versão [!DNL Commerce Data Export] [103.3.0](https://experienceleague.adobe.com/pt-br/docs/commerce-merchant-services/saas-data-export/release-notes#release-9), as assinaturas [!DNL Mview] em extensões personalizadas que usam extensões [!DNL Commerce Data Export] podem não funcionar corretamente.

Nesse caso, o erro *tabela não existe* ocorre porque o nome da tabela `catalog_data_exporter` foi alterado para `cde_products_feed` e você tem um código personalizado que faz referência ao nome antigo na assinatura [!DNL Data Exporter Mview].

## Solução

Na extensão personalizada, edite o arquivo de configuração [!DNL Mview] (```./etc/mview.xml```) para alterar o nome da tabela `catalog_data_exporter_products` para *`cde_products_feed`*.

O exemplo a seguir mostra o código que especifica as tabelas rastreadas pela assinatura [!DNL Mview]:

```
<view id="cde_products_feed" class="Magento\CatalogDataExporter\Model\Indexer\ProductFeedIndexer" group="indexer">
     <subscriptions>
         <table name="custom_table" entity_column="product_id" />
     </subscriptions>
</view>
```

## Leitura relacionada

* [[!DNL SaaS] Notas de Versão da Extensão de Exportação de Dados](https://experienceleague.adobe.com/pt-br/docs/commerce-merchant-services/saas-data-export/release-notes) no Guia de Exportação de Dados Adobe Commerce para Serviços [!DNL SaaS]
* [Práticas recomendadas para modificar tabelas de banco de dados](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) no Manual de implementação do Commerce
