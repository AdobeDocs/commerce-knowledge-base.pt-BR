---
title: "ACSD-49065: os itens de cotação não estão visíveis no administrador"
description: Aplique o patch ACSD-49065 para corrigir o problema do Adobe Commerce em que os itens de cotação não estão visíveis no administrador se estiverem atribuídos apenas ao estoque personalizado.
exl-id: 3a5ceb4c-4c94-4938-98d9-9171f2633056
feature: Admin Workspace, B2B, Orders, Quotes
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# ACSD-49065: os itens de cotação não estão visíveis no administrador

O patch ACSD-49065 corrige o problema em que os itens de cotação não estão visíveis no administrador se forem atribuídos apenas ao estoque personalizado. Este patch está disponível quando a variável [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.28 está instalado. A ID do patch é ACSD-49065. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3 - 2.4.6

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os itens de cotação não estarão visíveis no administrador se forem atribuídos somente ao estoque personalizado.

Pré-requisitos:

**[!UICONTROL B2B]** e **[!UICONTROL Inventory]** Os módulos do devem ser instalados.

<u>Etapas a serem reproduzidas</u>:

1. Ativar **[!UICONTROL Company]** e **[!UICONTROL B2B Quote]** em **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]**.
1. Criar um secundário **[!UICONTROL Inventory Source]** e atribua-o a um secundário **[!UICONTROL Inventory Stock]**.
1. Crie um novo produto atribuindo somente o secundário (não padrão) **[!UICONTROL Inventory Source]**.
1. Vá para a loja e crie uma nova conta de empresa. Efetue logon como **[!UICONTROL Company Admin]** e adicionar o produto criado ao carrinho.
1. Navegue até o carrinho e *[!UICONTROL Request a Quote]*.
1. Acesse o administrador e visualize a cotação solicitada em **[!UICONTROL Sales]** > **[!UICONTROL Quotes]**.

<u>Resultados esperados</u>:

Os itens ficam visíveis na nova cotação criada com os novos produtos sem salvar os produtos novamente.

<u>Resultados reais</u>:

A variável *[!UICONTROL Items Quoted]* seção está vazia. Se você salvar novamente o produto recém-criado, os itens serão exibidos.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.
