---
title: '"ACSD-48262: produtos não visíveis na loja quando [!UICONTROL Allow All Products Per Page] está definido [!UICONTROL Yes]'''
description: Aplique o patch ACSD-48262 para corrigir o problema do Adobe Commerce em que os produtos não estão visíveis na loja quando o [!UICONTROL Allow All Products Per Page] está definida como [!UICONTROL Yes].
exl-id: 327cad03-441d-4adb-8a10-802f06d3fcd1
feature: Admin Workspace, Cache, Categories, Orders, Products, Storefront
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 0%

---

# ACSD-48262: produtos não visíveis na loja quando [!UICONTROL Allow All Products Per Page] está definido *[!UICONTROL Yes]*

O patch ACSD-48262 corrige o problema em que os produtos não estão visíveis na loja quando o [!UICONTROL Allow All Products Per Page] está definida como *[!UICONTROL Yes]*. Este patch está disponível quando a variável [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.25 está instalado. A ID do patch é ACSD-48262. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) >=2.4.5 &lt; 2.4.6

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O patch ACSD-48262 corrige o problema em que os produtos não estão visíveis na loja quando o [!UICONTROL Allow All Products Per Page] está definida como *[!UICONTROL Yes]*.

<u>Etapas a serem reproduzidas</u>:

1. Criar uma categoria de teste.
1. Criar um produto de teste na categoria de teste.
1. Navegue pelo produto para testar a página de categorias na loja e verifique se o produto está visível.
1. Ir para **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** e defina o [!UICONTROL Allow All Products Per Page] configuração para *[!UICONTROL Yes]*.
1. Limpar cache.
1. Verifique a página de categoria na loja.

<u>Resultados esperados</u>:

O produto está visível.

<u>Resultados reais</u>:

O produto não está visível.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.


## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.
