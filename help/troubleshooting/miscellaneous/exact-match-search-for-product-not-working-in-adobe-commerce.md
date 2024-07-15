---
title: A pesquisa de correspondência exata não funciona no Adobe Commerce 2.4.x
description: Este artigo fornece um esclarecimento para o problema em que os resultados da pesquisa do store front usando a mesma sequência de pesquisa são diferentes no Adobe Commerce 2.4.x em comparação ao Adobe Commerce 2.3.x.
exl-id: 0867558e-1d74-4b83-abf3-651ca7fc32cb
feature: Products, Search
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '258'
ht-degree: 0%

---

# A pesquisa de correspondência exata não funciona no Adobe Commerce 2.4.x

Este artigo fornece um esclarecimento para o problema em que os resultados da pesquisa do store front usando a mesma sequência de pesquisa são diferentes no Adobe Commerce 2.4.x em comparação ao Adobe Commerce 2.3.x.

## Produtos e versões afetados

- Adobe Commerce (todos os métodos de implantação) 2.4.x, 2.3.x
- Live Search

## Problema

<u>Pré-requisitos:</u>

Você tem produtos com valores de atributo `Saga 1` e `Saga 16` em lojas Adobe Commerce 2.3 e Adobe Commerce 2.4.

<u>Etapas a serem reproduzidas:</u>

1. Na frente de uma loja habilitada para o Adobe Commerce 2.3, digite *Saga 1* no campo de pesquisa e clique em **Pesquisar**.
1. Observe que, nos resultados da pesquisa, você só obtém os produtos com o valor de atributo `Saga 1`.
1. Na frente de uma loja habilitada para o Adobe Commerce 2.4, digite *Saga 1* no campo de pesquisa e clique em **Pesquisar**.

<u>Resultado real:</u>

Os resultados da pesquisa na versão 2.4 incluem produtos com valores de atributo `Saga 1` e `Saga 16`.

<u>Resultado esperado:</u>

Os resultados da pesquisa na versão 2.4 são semelhantes à 2.3 e incluem apenas produtos com valor de atributo `Saga 1`.

## Causa

A funcionalidade de pesquisa nativa do Adobe Commerce usada na versão 2.3.x fornece resultados de pesquisa de correspondência exata. Enquanto o Live Search, um módulo opcional disponível para instalação, que foi lançado com o Adobe Commerce 2.4.x, é implementado de forma diferente, e o resultado real é o comportamento esperado quando o módulo é usado.

## Leitura relacionada

[Instale o Live Search](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html) em nosso guia do usuário.

[Live Search](https://devdocs.magento.com/live-search/overview.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=Live%20Search) em nossa documentação para desenvolvedores.
