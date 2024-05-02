---
title: "ACSD-45168: URLs amigáveis para SEO não geradas para produtos que têm atributos url_key substituídos"
description: Aplique o patch ACSD-45168 para corrigir o problema do Adobe Commerce, em que URLs amigáveis para SEO não gerados para produtos que têm atributos url_key substituídos no nível da visualização da loja.
exl-id: cdba42ac-3c96-439b-befa-f0a13587b5d9
feature: Attributes, Cache, Categories, Marketing Tools, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 0%

---

# ACSD-45168: URLs amigáveis para SEO não geradas para produtos que têm atributos url_key substituídos

O patch ACSD-45168 corrige o problema em que URLs amigáveis para SEO não são gerados para produtos que têm atributos url_key substituídos no nível de visualização da loja. Este patch está disponível quando a variável [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.24 está instalado. A ID do patch é ACSD-45168. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2 - 2.4.5-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

URLs compatíveis com SEO não são gerados para produtos que têm atributos url_key substituídos no nível de visualização da loja.

<u>Etapas a serem reproduzidas</u>:

1. Defina a configuração da seguinte maneira acessando o **[!UICONTROL Commerce Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Search Engine Optimization]**:
   * [!UICONTROL Use Categories Path for Product URLs] = *Sim*
   * [!UICONTROL Generate "category/product" URL Rewrites] = *Sim*
1. Limpe o cache de configuração.
1. Crie duas categorias: [!UICONTROL Category 1] e [!UICONTROL Category 2].
1. Crie dois produtos: [!UICONTROL Product 1] in [!UICONTROL Category 1], [!UICONTROL Product 2] in [!UICONTROL Category 1].
1. Alterar o escopo para [!UICONTROL Default Store View] para [!UICONTROL Product 1].
1. Desmarque o URL opcional [!UICONTROL Key] in [!UICONTROL Search Engine Optimization].
1. Salve o produto.
1. Voltar para [!UICONTROL All Store Views].
1. Adicionar [!UICONTROL Product 1] para [!UICONTROL Category 2], e adicione [!UICONTROL Product 2] para [!UICONTROL Category 2].
1. Verifique a [!UICONTROL url_rewrite] tabela ou [!UICONTROL Marketing] > [!UICONTROL SEO & Search] > [!UICONTROL URL Rewrites].

<u>Resultados esperados</u>:

O URL compatível com SEO para [!UICONTROL Category 2] é criado para [!UICONTROL Product 1].

<u>Resultados reais</u>:

O URL compatível com SEO para [!UICONTROL Category 2] está ausente para [!UICONTROL Product 1] porque o atributo de chave URL foi substituído pelo escopo de exibição de loja.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.
