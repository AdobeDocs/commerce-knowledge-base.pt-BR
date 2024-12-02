---
title: '[!UICONTROL Recommendations] [!DNL JS] erros após a atualização para o Adobe Commerce versão 2.4.5'
description: Este artigo fornece uma correção para quando, após a atualização para o Adobe Commerce (todos os métodos de implantação), há  [!DNL JS] erros no console relacionados aos módulos do produto [!UICONTROL Recommendations].
feature: Install, Upgrade
role: Developer
exl-id: 51d899eb-48f7-48c5-8bda-bd72a4d28945
source-git-commit: 8b6bf1cdada7edb0cdb0bb3e90ed15ee8cebf77e
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

O problema é causado porque a página da loja ainda se refere a alguns módulos/unidades (blocos e/ou widgets) do produto excluído [!UICONTROL Recommendations] em sua página inicial [!DNL CMS].

<u>Etapas a serem reproduzidas</u>:

1. Atualize para o Adobe Commerce 2.4.5.
1. Acesse a página da loja na Web.
1. Clique com o botão direito do mouse e selecione **Inspect** para abrir o Inspetor Web no seu navegador.
1. Clique na guia **[!UICONTROL Console]**.
1. Revise os erros [!DNL JS].

<u>Resultados esperados</u>:

Atualização bem-sucedida sem erros [!DNL JS].

<u>Resultados reais</u>:

Vários tipos diferentes de erros [!DNL JS] são exibidos no console do navegador da Web.

## Solução alternativa

Como solução alternativa, você pode revisar todas as [!UICONTROL Recommendations] unidades usadas na página e remover todas as unidades excluídas.
