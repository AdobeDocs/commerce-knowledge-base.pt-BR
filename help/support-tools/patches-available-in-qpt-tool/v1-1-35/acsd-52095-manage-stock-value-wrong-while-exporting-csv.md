---
title: "ACSD-52095: o gerenciamento do valor de estoque está incorreto ao exportar CSV"
description: Aplique o patch ACSD-52095 para corrigir o problema do Adobe Commerce em que o valor do estoque de gerenciamento de produtos está incorreto ao exportar CSV.
feature: Inventory, Products
role: Admin, Developer
exl-id: 9e599931-e9b1-4216-b78d-3993d9c3132d
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# ACSD-52095: [!UICONTROL Manage Stock] o valor está incorreto ao exportar CSV

O patch ACSD-52095 corrige o problema em que o produto `manage_stock` O valor de está incorreto ao exportar CSV. Este patch está disponível quando a variável [!DNL Quality Patches Tool (QPT)] O 1.1.35 está instalado. A ID do patch é ACSD-52095. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.7 - 2.4.5-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A variável `manage_stock` O valor de está incorretamente definido como 0 no arquivo CSV após a exportação do produto.

<u>Etapas a serem reproduzidas</u>:

1. Ir para **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Product Stock Options]** e defina **[!UICONTROL Manage Stock]** = *[!UICONTROL No]*.
1. Crie um novo produto e salve.
1. Ir para **[!UICONTROL System]** > **[!UICONTROL Export]**.
1. Selecionar *[!UICONTROL Entity Type]* = *[!UICONTROL Products]* e exportar os produtos.
1. Verifique o arquivo CSV gerado: `manage_stock` = 0, `use_config_manage_stock` = 1.
1. Mais uma vez, vá para **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Product Stock Options]** e defina  **[!UICONTROL Manage Stock]** = *[!UICONTROL Yes]*.
1. Ir para **Sistema** > **Exportar**.
Selecionar *[!UICONTROL Entity Type]* = *[!UICONTROL Products and export the products]*.
1. Verifique o arquivo CSV gerado: `manage_stock` = 0, `use_config_manage_stock` = 1.
1. Abra o produto no Administrador e vá para **[!UICONTROL Advanced Inventory]** e verifique a **[!UICONTROL Manage Stock]** valor.

<u>Resultados esperados</u>

A variável **[!UICONTROL Manage Stock]** o valor é *1* quando estiver ativado para os produtos.

<u>Resultados reais</u>

A variável **[!UICONTROL Manage Stock]** o valor é *0* quando estiver ativado para os produtos.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) no [!DNL Quality Patches Tool] guia.
