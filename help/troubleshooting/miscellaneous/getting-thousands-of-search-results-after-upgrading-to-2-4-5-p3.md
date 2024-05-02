---
title: Obter milhares de resultados ao procurar um produto específico
description: Este artigo fornece uma solução para o problema em que você obtém milhares de resultados de pesquisa quando procura um produto específico.
feature: Quotes, Search, Returns
role: Developer, Admin
exl-id: 0eccf212-96be-4ea5-9e6e-95f27d7d9f92
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '185'
ht-degree: 0%

---

# Obter milhares de resultados ao procurar um produto específico

Este artigo fornece uma solução para o problema em que você obtém milhares de resultados de pesquisa ao procurar um produto específico.

## Produtos e versões afetados

* Todas as versões do Adobe Commerce com [!DNL ElasticSearch] instalado

## Problemas

Você está procurando um produto específico (por exemplo, *WSH12-32-Vermelho*), mas a pesquisa retorna muitos produtos semelhantes.

## Soluções

A natureza de uma pesquisa de texto completo no [!DNL ElasticSearch] é baseado na relevância, não na correspondência exata. Portanto, as correspondências mais relevantes (como SKU com correspondência exata) são solicitadas primeiro.

No entanto, se você precisar de um resultado de pesquisa que corresponda exatamente ao termo de pesquisa (correspondência exata), você deve usar aspas para a consulta de pesquisa. Por exemplo, query para *WSH12-32-Vermelho* sem aspas retornará vários resultados com a correspondência exata (produto com *SKU WSH12-32-Vermelho*) que aparece primeiro no resultado. Mas consulta citada *&quot;WSH12-32-Vermelho&quot;* retornará apenas um resultado de correspondência exata.
