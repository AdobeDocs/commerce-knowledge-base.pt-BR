---
title: Índices invalidados e "indexer_reindex_all_invalid" são executados constantemente
description: Índices invalidados e "indexer_reindex_all_invalid" são executados constantemente
labels: troubleshooting,error,indexing,crons,site performance,adobe commerce,magento,cron,indexer_reindex_all_invalid,SQL,MySQL,reindex
exl-id: c7148ef4-2155-4d4c-869b-1d08de4af598
feature: B2B, Catalog Management, Categories, Observability, Price Indexer
role: Developer
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# Índices invalidados e `indexer_reindex_all_invalid` executados constantemente

Este artigo fornece uma possível solução alternativa para o problema em que o site tem problemas de desempenho causados por reindexação constante. Isso é causado pelo trabalho [!DNL cron] `indexer_reindex_all_invalid` em execução contínua e pelos caches limpos em [!DNL reindex].

## Produtos e versões afetados

* Adobe Commerce (nuvem e no local) 2.4.0+ (Como **[!UICONTROL Category Permissions]** é um recurso exclusivo do Adobe-Commerce, ele não afetará o Magento Open Source.)

## Problema

No [!DNL New Relic One] os logs de erro devem mostrar `indexer_update_all_views` em execução várias vezes com um tempo > 1 segundo (isto é, ele está processando algo).

## Causa

Quando o importador principal do Adobe Commerce é executado (manualmente ou por [!DNL cron]), um conjunto de plug-ins em vários módulos principais é executado para determinar quais índices devem ser invalidados.

O problema ocorre quando o módulo **[!UICONTROL Category Permissions]** está habilitado no [!DNL Commerce Admin]. Se isso for verdadeiro, o plug-in do módulo sempre invalida os índices Produto e Categoria (e índices vinculados) quando uma importação é executada. Se os tipos de importação padrão forem examinados, todos eles afetarão **[!UICONTROL Category Permissions]**. Invalidação esperada.

Além disso, quando um site tiver módulos B2B habilitados, se **[!UICONTROL Shared Catalog]** estiver ativado, ele será ativado e bloqueará **[!UICONTROL Category Permissions]**. Desativar **[!UICONTROL Shared Catalog]** desbloqueará **[!UICONTROL Category Permissions]**, mas não o desativará.

<u>Verificando [!DNL cron] logs no banco de dados [!DNL MySQL]</u>:

Se você fizer logon no banco de dados [!DNL MySQL], eles poderão verificar o log `cron` para o processo **[!DNL reindex all indexes]**.
Este **deveria** aparecer várias vezes, mas o fator importante é que o processo faz uma de duas coisas possíveis.

O processo só pode executar uma destas duas ações:

1. Nada: levaria de 0 a 1 segundo (um segundo ou menos) - o processo verifica se precisa fazer algo e pára se não precisa fazer nada.
1. [!DNL Reindex] tudo: Sempre levará tempo - normalmente alguns minutos.

Normalmente, você gostaria de ver muitas ocorrências do processo, mas com um tempo de execução de menos de um segundo.
Um comerciante pode, portanto, usar esta consulta [!DNL MySQL] para localizar transações que levam **mais de 1 segundo** para serem executadas:

```sql
SELECT TIMESTAMPDIFF(SECOND, executed_at, finished_at) AS period FROM cron_schedule WHERE job_code = 'indexer_reindex_all_invalid' HAVING period > 1
```

Você pode ver por quanto tempo um período é registrado executando:

```sql
SELECT executed_at FROM cron_schedule WHERE job_code = 'indexer_reindex_all_invalid' AND executed_at IS NOT NULL ORDER BY executed_at ASC LIMIT 1;
```

Se isso não lhe der um período suficientemente longo para fazer uma avaliação adequada, você pode aumentar o tempo que um processo `cron` bem-sucedido será mantido no log seguindo este guia [[!DNL Cron] (tarefas agendadas)](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/cron.html?lang=pt-BR) e aumentando o valor **[!DNL Success History Lifetime]** (o padrão é apenas 60 minutos).


## Solução

Estenda `Magento\CatalogPermissions\Model\Indexer\Plugin\Import` para que o método `afterImportSource` exclua o importador personalizado.

```
    public function afterImportSource(\Magento\ImportExport\Model\Import $subject, $import)
    {
        if ($this->config->isEnabled() && $subject->getEntity() !== 'ENTITY_CODE') {
            $this->indexerRegistry->get(\Magento\CatalogPermissions\Model\Indexer\Category::INDEXER_ID)->invalidate();
            $this->indexerRegistry->get(\Magento\CatalogPermissions\Model\Indexer\Product::INDEXER_ID)->invalidate();
        }
        return $import;
    }
```

Onde `ENTITY_CODE` é o valor usado para o parâmetro de nome de entidade no arquivo `import.xml` para o importador personalizado.

## Leitura relacionada

[Configurar [!DNL cron] trabalhos](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs.html?lang=pt-BR) no Guia de Configuração de Operações do Adobe Commerce.
