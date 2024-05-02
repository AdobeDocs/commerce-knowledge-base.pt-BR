---
title: '[!UICONTROL Recommendations] [!DNL JS] erros após a atualização para o Adobe Commerce versão 2.4.5'
description: Este artigo fornece uma correção para quando, após a atualização para o Adobe Commerce (todos os métodos de implantação), há [!DNL JS] erros no console relacionados ao produto [!UICONTROL Recommendations] módulos.
feature: Install, Upgrade
role: Developer
exl-id: 51d899eb-48f7-48c5-8bda-bd72a4d28945
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '200'
ht-degree: 0%

---

# [!UICONTROL Recommendations] [!DNL JS] erros após a atualização para o Adobe Commerce versão 2.4.5

Este artigo fornece uma correção para quando, após a atualização para o Adobe Commerce (todos os métodos de implantação), há [!DNL JS] erros no console relacionados ao produto [!UICONTROL Recommendations] módulos/unidades.

No momento, não há planos para resolver esse problema em versões futuras.

## Versões e produtos afetados

* Adobe Commerce (todos os métodos de implantação) ao atualizar para a versão 2.4.5

## Problema

O problema é causado pela página da loja que ainda se refere a algum produto excluído [!UICONTROL Recommendations] módulos/unidades (blocos e/ou widgets) em sua home page [!DNL CMS].

<u>Etapas a serem reproduzidas</u>:

1. Atualize para o Adobe Commerce 2.4.5.
1. Acesse a página da loja na Web.
1. Clique com o botão direito do mouse e selecione **Inspect** para abrir o inspetor da web no navegador da web.
1. Clique em **[!UICONTROL Console]** guia.
1. Revise o [!DNL JS] erros.

<u>Resultados esperados</u>:

Atualização bem-sucedida sem [!DNL JS] erros.

<u>Resultados reais</u>:

Vários tipos diferentes de [!DNL JS] os erros são exibidos no console do navegador da web.

## Solução alternativa

Como solução alternativa, você pode revisar todas as [!UICONTROL Recommendations] unidades usadas na página e remover as unidades excluídas.
