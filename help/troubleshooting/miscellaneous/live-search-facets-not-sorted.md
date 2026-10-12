---
title: '[!DNL Live Search] facetas não estão classificadas alfabeticamente'
description: Este artigo fornece informações sobre solução de problemas se os aspectos [!DNL Live Search] não estiverem classificados alfabeticamente.
feature: Admin Workspace, Categories, Search
role: Developer
exl-id: 59f86727-c2a6-4418-8753-40f7937e059c
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
subfeature_v2:
  - id: bb2df8be-afdd-4818-b6b5-95ca1dd3bc3a
    internal-label: Admin workspace
  - id: e91a50b1-0b31-436e-9033-00e4776e94cb
    internal-label: Categories
  - id: a1d22079-48b9-5e69-9ee6-eb236068ef34
    internal-label: Search
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '146'
ht-degree: 0%
---
# [!DNL Live Search] facetas não estão classificadas alfabeticamente

## Produtos e versões afetados

Adobe Commerce versões 2.4.x e mais recentes

## Problema

Todas as facetas de vitrine do Adobe Commerce são classificadas alfabeticamente com opções de seleção única, independentemente do tipo de entrada atribuído ao atributo correspondente.

## Solução alternativa

No entanto, em certos casos de borda, os aspectos podem não ser classificados alfabeticamente como configurado no [[!DNL Live Search] espaço de trabalho de facetas](https://experienceleague.adobe.com/pt-br/docs/commerce-merchant-services/live-search/live-search-admin/facets/faceting-workspace).

Como solução alternativa, você pode classificar atributos de produto na seção de atributos [!UICONTROL Admin].

1. Na barra lateral **[!UICONTROL Admin]**, vá para **Lojas** > *Atributos* > **Produto**.
1. Selecione um atributo na tabela.

   ![Lista de Atributos](assets/attribute-list.png)

1. Abra o atributo que tem os valores que você deseja classificar e selecione **Informações do Atributo** > **Propriedades**.
1. Em **Gerenciar Opções**, você pode classificar os valores do atributo.

   ![Classificar atributos](assets/sort-attributes.png)
