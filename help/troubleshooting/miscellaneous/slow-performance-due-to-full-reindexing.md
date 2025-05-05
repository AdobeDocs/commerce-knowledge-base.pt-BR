---
title: Desempenho lento devido à reindexação completa
description: Este artigo fornece uma correção para um desempenho insatisfatório devido à reindexação completa (em que os dados nas tabelas do banco de dados relacionadas à indexação estão sendo atualizados).
exl-id: 4f20a862-cf54-4196-8a88-101f0c80f8f1
feature: Best Practices
role: Developer
source-git-commit: 72ee49a8667f575a58e0cf1b3d5c9df936cc628b
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# Desempenho lento devido à reindexação completa

Este artigo fornece uma correção para um desempenho insatisfatório devido à reindexação completa (em que os dados nas tabelas do banco de dados relacionadas à indexação estão sendo atualizados).

## Versões e produtos afetados

* Adobe Commerce na infraestrutura em nuvem 2.x.x
* Adobe Commerce no local 2.x.x

### Problema

A limpeza e a reconstrução constante do índice são algumas das razões para a degradação do desempenho. Além disso, a reindexação completa constante adiciona bloqueios em tabelas, fazendo com que o site funcione muito mais lentamente do que o esperado.

### Causa

As ações que podem produzir reindexação completa foram executadas pelo administrador, incluindo:

* Salvamento do atributo do produto
* Salvar exibição de site/loja/loja
* Armazenar configuração

>[!NOTE]
>
>Essas ações devem ser executadas fora do horário comercial para garantir que essas ações não afetem o desempenho durante o horário comercial.

[Extensões de terceiros](https://support.magento.com/hc/en-us/articles/360042361152-Best-Practices-for-using-third-party-extensions-in-Magento) também podem causar reindexação completa. A reindexação completa também pode ser executada manualmente da CLI. Para descobrir se você tem índices sendo reindexados e possivelmente causando downgrade de desempenho:

1. Execute esta consulta para localizar os indexadores que foram totalmente reindexados nos últimos 15 minutos:

   ```
   SELECT * FROM indexer_state WHERE updated > NOW() - INTERVAL 15 MINUTE;
   ```

   Um nome de indexador na saída significa que ele foi reindexado pelo menos uma vez durante os últimos 15 minutos.

1. Se você encontrar reindexação completa frequente, investigue o seguinte:
   * Quem pode estar fazendo isso manualmente na CLI
   * Qual módulo de terceiros está fazendo a reindexação
   * Que módulo de terceiros está marcando indexadores como *Inválido*

### Solução

Execute a reindexação somente quando necessário. Para ver as etapas, consulte [Configurar indexadores](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/configuration-guide/cli/manage-indexers#configure-indexers) em nossa documentação para desenvolvedores. Uma recomendação geral e a prática recomendada é permitir que o mecanismo de reindexação parcial cuide da reindexação de dados sem a necessidade de ação manual de um comerciante. Toda reindexação deve ser feita usando a funcionalidade nativa do Adobe Commerce (Mview). O Mview executa a reindexação parcial, que é a maneira mais eficiente de reindexar dados. Para saber mais sobre o Mview, consulte [Visão geral de indexação: Mview](https://developer.adobe.com/commerce/php/development/components/indexing/#mview) em nossa documentação para desenvolvedores.

## Leitura relacionada

* [Visão geral da indexação: como reindexar](https://developer.adobe.com/commerce/php/development/components/indexing/#how-to-reindex) em nossa documentação do desenvolvedor.
* [O cache invalidado causa degradação do tempo de resposta](/help/troubleshooting/miscellaneous/invalidated-cache-causes-response-time-degradation.md) em nossa base de dados de conhecimento de suporte.

