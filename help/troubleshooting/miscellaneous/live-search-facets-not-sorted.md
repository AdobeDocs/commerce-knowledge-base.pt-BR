---
title: '[!DNL Live Search] facetas não estão classificadas alfabeticamente'
description: Este artigo fornece informações sobre a solução de problemas se os aspectos  [!DNL Live Search]  não estiverem classificados em ordem alfabética.
feature: Admin Workspace, Categories, Search
role: Developer
exl-id: 59f86727-c2a6-4418-8753-40f7937e059c
source-git-commit: 9bb839292a120a3dab5151d493f915619dbf5c06
workflow-type: tm+mt
source-wordcount: '130'
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
