---
title: Obter milhares de resultados ao procurar um produto específico
description: Este artigo fornece uma solução para o problema em que você obtém milhares de resultados de pesquisa quando procura um produto específico.
feature: Quotes, Search, Returns
role: Developer, Admin
exl-id: 0eccf212-96be-4ea5-9e6e-95f27d7d9f92
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 792a7e9b-6519-5e99-a913-56c3dd2408da
    internal-label: Quotes
  - id: ac07462c-732c-5c1c-947b-4ce533b4fcfb
    internal-label: Returns
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
subfeature_v2:
  - id: a1d22079-48b9-5e69-9ee6-eb236068ef34
    internal-label: Search
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '190'
ht-degree: 0%
---
# Obter milhares de resultados ao procurar um produto específico

Este artigo fornece uma solução para o problema em que você obtém milhares de resultados de pesquisa ao procurar um produto específico.

## Produtos e versões afetados

* Adobe Commerce todas as versões com [!DNL ElasticSearch] instalado

## Problemas

Você está procurando um produto específico (por exemplo, *WSH12-32-Red*), mas a pesquisa retorna muitos produtos semelhantes.

## Soluções

A natureza de uma pesquisa de texto completo em [!DNL ElasticSearch] é baseada na relevância, não na correspondência exata. Portanto, as correspondências mais relevantes (como SKU com correspondência exata) são solicitadas primeiro.

No entanto, se você precisar de um resultado de pesquisa que corresponda exatamente ao termo de pesquisa (correspondência exata), você deve usar aspas para a consulta de pesquisa. Por exemplo, a consulta para *WSH12-32-Red* sem aspas retornará vários resultados com a correspondência exata (produto com *SKU WSH12-32-Red*) aparecendo primeiro no resultado. Mas a consulta citada *&quot;WSH12-32-Red&quot;* retornará apenas um resultado de correspondência exata.
