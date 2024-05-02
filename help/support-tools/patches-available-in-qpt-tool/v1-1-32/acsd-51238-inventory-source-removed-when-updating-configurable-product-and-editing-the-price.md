---
title: "ACSD-51238: a origem do inventário é removida ao atualizar um produto configurável e editar o preço"
description: Aplique o patch ACSD-51238 para corrigir o problema do Adobe Commerce em que a origem do inventário é removida ao atualizar um produto configurável e editar o preço.
exl-id: ab2f60fd-5da3-45f7-a489-6f4f9d34e1f1
feature: Configuration, Inventory, Orders, Products
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 0%

---

# ACSD-51238: A origem do inventário é removida ao atualizar um produto configurável e editar o preço

O patch ACSD-51238 corrige o problema em que a origem do inventário é removida ao atualizar um produto configurável e editar o preço. Este patch está disponível quando a variável [!DNL Quality Patches Tool (QPT)] O 1.1.32 está instalado. A ID do patch é ACSD-51238. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.6

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A origem do inventário é removida ao atualizar um produto configurável e editar o preço.

<u>Etapas a serem reproduzidas</u>:

1. Instalar **[!DNL Adobe Commerce]** com **[!DNL Inventory module]**
1. Vá para a **[!UICONTROL Admin]** -> **[!UICONTROL Stores]** -> **[!UICONTROL Inventory]** e criar *duas fontes* e *duas ações*.
1. Criar um **[!UICONTROL configurable product]** e atribuí-lo a **[!UICONTROL default sources]** ou **[!UICONTROL newly created sources]**.
1. Clique no link **[!UICONTROL next button]** e *save* o produto.
1. Agora, edite as mesmas **[!UICONTROL Configurable Product]** e clique em **[!UICONTROL Edit Configuration]** dentro do **[!UICONTROL Configuration tab]**.
1. Entrada `Step 3: Bulk Images,Price and Quantity`, altere o `price` e sair `Quantity` e `Images` para `Skip quantity at this time` e `Skip image uploading at this time` respectivamente.
1. Clique em **[!UICONTROL next button]** e gerar o produto.

<u>Resultados esperados</u>

A quantidade por origem dentro do **[!UICONTROL Configuration tab]** não deve ficar em branco.

<u>Resultados reais</u>

A quantidade por origem dentro do **[!UICONTROL Configuration tab]** está vazio.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) no [!DNL Quality Patches Tool] guia.
