---
title: 'ACSD-51238: A origem do inventário é removida ao atualizar um produto configurável e editar o preço'
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

O patch ACSD-51238 corrige o problema em que a origem do inventário é removida ao atualizar um produto configurável e editar o preço. Este patch está disponível quando o [!DNL Quality Patches Tool (QPT)] 1.1.32 está instalado. A ID do patch é ACSD-51238. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.6

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR>). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A origem do inventário é removida ao atualizar um produto configurável e editar o preço.

<u>Etapas a serem reproduzidas</u>:

1. Instalar **[!DNL Adobe Commerce]** com **[!DNL Inventory module]**
1. Vá para **[!UICONTROL Admin]** -> **[!UICONTROL Stores]** -> **[!UICONTROL Inventory]** e crie *duas fontes* e *duas ações*.
1. Crie um **[!UICONTROL configurable product]** e atribua-o a **[!UICONTROL default sources]** ou **[!UICONTROL newly created sources]**.
1. Clique no **[!UICONTROL next button]** e *salve* o produto.
1. Agora edite o mesmo **[!UICONTROL Configurable Product]** e clique em **[!UICONTROL Edit Configuration]** dentro de **[!UICONTROL Configuration tab]**.
1. Em `Step 3: Bulk Images,Price and Quantity`, altere o `price` e deixe `Quantity` e `Images` para `Skip quantity at this time` e `Skip image uploading at this time`, respectivamente.
1. Clique em **[!UICONTROL next button]** e gere o produto.

<u>Resultados esperados</u>

A quantidade por origem dentro de **[!UICONTROL Configuration tab]** não deve estar vazia.

<u>Resultados reais</u>

A quantidade por origem dentro de **[!UICONTROL Configuration tab]** está vazia.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=pt-BR>) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] versão: uma nova ferramenta para autoatender patches de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando o [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR>) no guia [!DNL Quality Patches Tool].
