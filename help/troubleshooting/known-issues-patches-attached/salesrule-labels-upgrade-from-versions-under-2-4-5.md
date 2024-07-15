---
title: Problemas de rótulos '**[!UICONTROL salesRules]** ao atualizar de versões < 2.4.5'
description: Aplique um patch para lidar com os problemas **[!UICONTROL salesRules]** ao atualizar das versões do Adobe Commerce < 2.4.5.
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 0%

---

# Problemas de rótulos de **[!UICONTROL salesRules]** ao atualizar de versões &lt; 2.4.5

A funcionalidade de preparo de rótulos **[!UICONTROL salesRules]** foi introduzida na Adobe Commerce [2.4.5](/docs/commerce-operations/release/notes/adobe-commerce/2-4-5.html). A alteração pode levar a problemas ao atualizar do Adobe Commerce &lt; 2.4.5 para qualquer versão >= 2.4.5. Após a atualização, há uma possibilidade de **[!UICONTROL salesRules]** rótulos serem incompatíveis. Para resolver o problema, um patch deve ser aplicado logo após a atualização para uma versão mais recente do Adobe Commerce.

## Produtos e versões afetados

Adobe Commerce na infraestrutura em nuvem &lt; 2.4.5

## Correção

Use o seguinte patch anexado:

[ACSD-50625_2.4.5-P1.patch.zip](assets/ACSD-50625_2.4.5-p1.patch.zip)

## Como aplicar o patch

1. Siga as etapas em [Executar uma atualização](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/implementation/perform-upgrade.html) no guia do Commerce.
1. Aplicar o patch anexado antes da fase **[!UICONTROL Update metadata]**.
(Você também pode aplicar o patch depois de concluir a fase **[!UICONTROL Update metadata]**, mas precisa executar `bin/magento setup:upgrade` novamente).
1. Continue com o restante das etapas em [Executar uma atualização](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/implementation/perform-upgrade.html).
