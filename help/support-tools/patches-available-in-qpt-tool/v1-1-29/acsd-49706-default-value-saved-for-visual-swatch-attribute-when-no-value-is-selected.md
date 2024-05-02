---
title: "ACSD-49706: valor padrão salvo para o atributo de amostra visual quando nenhum valor é selecionado"
description: Aplique o patch ACSD-49706 para corrigir o problema do Adobe Commerce em que um valor padrão é salvo para um atributo de amostra visual quando nenhum valor é selecionado.
exl-id: fe6071df-f2a4-443a-acfa-67f3d253c5e4
feature: Admin Workspace, Attributes
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 0%

---

# ACSD-49706: Valor padrão salvo para o atributo de amostra visual quando nenhum valor é selecionado

O patch ACSD-49706 corrige o problema em que um valor padrão é salvo para um atributo de amostra visual quando nenhum valor é selecionado. Este patch está disponível quando a variável [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.29 está instalado. A ID do patch é ACSD-49706. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.7 - 2.4.6

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Um valor padrão é salvo para um atributo de amostra visual quando nenhum valor é selecionado.

<u>Etapas a serem reproduzidas</u>:

1. Ir para **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]**.
1. Clique em **[!UICONTROL Add New Attribute]**.
1. Preencha os campos.

   * Por exemplo, escolha o tipo de entrada *[!UICONTROL Visual Swatch]* e adicionar várias opções (como *Vermelho*, *Verde*). Escolha uma dessas opções como padrão.
   * Clique em **[!UICONTROL Save Attribute]**.

1. Ir para **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Attribute Set]**.
1. Edite o *[!UICONTROL Default]* conjunto de atributos.
1. Mover *[!UICONTROL New Attribute]* da coluna *[!UICONTROL Unassigned Attributes]* para o *[!UICONTROL Product Details]* pasta na coluna do meio.

   * Clique em **[!UICONTROL Save]**.

1. Crie um novo produto usando o *[!UICONTROL Default]* conjunto de atributos.

   * Deixe a *[!UICONTROL New Attribute]* esvazie e salve.

1. Depois de salvo, um valor aparece no *[!UICONTROL New Attribute]*.

<u>Resultados esperados</u>:

Nenhum valor é atribuído a *[!UICONTROL New Attribute]* por padrão.

<u>Resultados reais</u>:

Um valor padrão é aplicado ao atributo ao salvar um produto.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.
