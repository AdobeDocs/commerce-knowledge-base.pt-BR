---
title: O status do índice de Elasticsearch é 'amarelo' ou 'vermelho'
description: O artigo fornece uma correção para quando o Status do índice de Elasticsearch não é '*verde*'. '*amarelo*' indica normal e '*vermelho*' indica ruim. O status "amarelo" ou "vermelho" pode ocorrer em conjunto com produtos ausentes ou com a exibição de informações antigas do produto.
exl-id: 27689511-6a41-41a9-8dda-a627d2f65263
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '283'
ht-degree: 0%

---

# O status do índice de Elasticsearch é &#39;amarelo&#39; ou &#39;vermelho&#39;

>[!WARNING]
>
> [O mecanismo de pesquisa do catálogo MySQL será removido no Adobe Commerce 2.4.0](/help/announcements/adobe-commerce-announcements/mysql-catalog-search-engine-will-be-removed-in-magento-2-4-0.md). Você deve ter o Elasticsearch host configurado antes de instalar a versão 2.4.0. Consulte [Instalar e configurar o Elasticsearch](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/search/overview-search).

O artigo fornece uma correção para quando o Status do Índice Elasticsearch não é &#39;*green*&#39;. &#39;*amarelo*&#39; indica normal, e &#39;*vermelho*&#39; indica ruim. O status &quot;amarelo&quot; ou &quot;vermelho&quot; pode ocorrer em conjunto com produtos ausentes ou com a exibição de informações antigas do produto.

## Versões e produtos afetados

* Adobe Commerce na infraestrutura em nuvem 2.2.x, 2.3.x
* Adobe Commerce no local 2.2.x, 2.3.x

## Problema

O índice de pesquisa do catálogo de Elasticsearch está lento, resultando em um status de &#39;*amarelo*&#39; ou &#39;*vermelho*&#39; em vez de &#39;*verde*&#39;. Você também pode experimentar alterações ausentes no front-end.

## Causa

Pode haver várias causas em potencial. Uma causa é a instância de Elasticsearch ficar sem espaço em disco. Outra causa são os índices duplicados.

## Solução

Crie um novo despejo mysql antes de seguir essas etapas e execute-as fora do horário comercial para evitar afetar potencialmente seus clientes:

1. Alternar temporariamente para pesquisa MySQL - habilitar pesquisa MySQL. (Observação: lembre-se de voltar para o Elasticsearch ou você pode ter problemas de desempenho).
1. Para identificar índices duplicados, execute o seguinte comando:

   ```
   curl --silent -X GET localhost:9200/_cat/indices?v
   ```

1. Para excluir índices:

   ```
   curl -XDELETE localhost:9200/[your_index_name_here]
   ```

1. Reative o Elasticsearch.
1. Executar reindexação completa.
1. Verifique o status dos índices executando o seguinte comando:

   ```
   curl --silent -X GET localhost:9200/_cat/indices?v
   ```

Se essas etapas não funcionarem, [envie um tíquete de suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

## Leitura relacionada

Para saber mais, consulte a [API de integridade do cluster Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/cluster-health.html).
