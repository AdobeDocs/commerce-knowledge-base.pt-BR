---
title: '**[!UICONTROL salesRules]** problemas de rótulos ao atualizar das versões < 2.4.5'
description: Aplique um patch para lidar com o **[!UICONTROL salesRules]** problemas ao atualizar das versões do Adobe Commerce < 2.4.5.
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 0%

---

# **[!UICONTROL salesRules]** problemas de rótulos ao atualizar das versões &lt; 2.4.5

A variável **[!UICONTROL salesRules]** a funcionalidade de preparo de rótulo foi introduzida no Adobe Commerce [2.4.5](/docs/commerce-operations/release/notes/adobe-commerce/2-4-5.html). A alteração pode levar a problemas ao atualizar do Adobe Commerce &lt; 2.4.5 para qualquer versão >= 2.4.5. Após a atualização, há a possibilidade de que **[!UICONTROL salesRules]** os rótulos são incompatíveis. Para resolver o problema, um patch deve ser aplicado logo após a atualização para uma versão mais recente do Adobe Commerce.

## Produtos e versões afetados

Adobe Commerce na infraestrutura em nuvem &lt; 2.4.5

## Correção

Use o seguinte patch anexado:

[ACSD-50625_2.4.5-P1.patch.zip](assets/ACSD-50625_2.4.5-p1.patch.zip)

## Como aplicar o patch

1. Siga as etapas em [Executar uma atualização](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/implementation/perform-upgrade.html) no guia do Commerce.
1. Aplique o patch anexado antes do **[!UICONTROL Update metadata]** fase.
(Você também pode aplicar o patch depois de ter concluído a **[!UICONTROL Update metadata]** fase, mas é necessário executar `bin/magento setup:upgrade` mais uma vez).
1. Continue com o restante das etapas em [Executar uma atualização](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/implementation/perform-upgrade.html).
