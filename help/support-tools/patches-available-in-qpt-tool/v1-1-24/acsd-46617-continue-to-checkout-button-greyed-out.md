---
title: '"ACSD-46617: **[!UICONTROL Continue to Checkout]** botão esmaecido quando o subtotal é maior que o valor mínimo de pedido configurado'''
description: Aplique o patch ACSD-46617 para resolver o problema do Adobe Commerce em que o **[!UICONTROL Continue to Checkout]** estará esmaecido mesmo se o subtotal for maior que o valor mínimo configurado para o pedido.
exl-id: 42fe02bd-f48b-4c6d-8643-ea2c1aa98c94
feature: Checkout, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---

# ACSD-46617: &quot;[!UICONTROL Continue to Checkout]O botão &quot; fica esmaecido quando o subtotal é maior que &quot;[!UICONTROL Minimum Order Amount]&quot;

Este patch ACSD-46617 resolve o problema em que o **[!UICONTROL Continue to Checkout]** fica esmaecido mesmo se o subtotal for maior que o valor mínimo configurado para o pedido. Este patch está disponível quando a variável [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.24 está instalado. A ID do patch é ACSD-46617. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A variável **[!UICONTROL Continue to Checkout]** fica esmaecido mesmo se o subtotal for maior que o valor mínimo configurado para o pedido.

<u>Etapas a serem reproduzidas</u>:

1. Acesse o Administrador do Adobe Commerce > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Minimum Order Amount]** e defina o seguinte:
   * [!UICONTROL Enable]: *[!UICONTROL Yes]*
   * 
     [!UICONTROL Minimum Amount]: *2*

1. Criar um [!UICONTROL Cart Price Rule].
   * [!UICONTROL Coupon Code]: *[!UICONTROL TEST (optional)]*
   * [!UICONTROL Conditions]: *[!UICONTROL Keep empty]*
   * [!UICONTROL Actions]:
      * [!UICONTROL Apply]: *[!UICONTROL Percent of product price discount]*
      * 
        [!UICONTROL Discount Amount]: *92*
      * [!UICONTROL Apply to Shipping Amount]: *[!UICONTROL Yes]*
1. Crie um produto com o preço de US$ 25.
1. Adicione o produto ao carrinho.
1. Vá para o carrinho de compras e selecione o valor de US$ 5 **[!UICONTROL Flat Rate shipping]** e aplique o código do cupom.
1. Acesse o checkout, conclua o envio e navegue até o **[!UICONTROL Paytment]** seção.
1. Volte para o carrinho de compras.

<u>Resultados esperados</u>:

Não há erro relacionado ao valor mínimo do pedido, pois o total geral de US$ 2,4 é maior que o valor necessário de US$ 2.

<u>Resultados reais</u>:

* Há um erro relacionado ao valor mínimo do pedido mesmo quando o total geral de US$ 2,4 é maior que o valor mínimo do pedido de US$ 2.
* A variável **[!UICONTROL Continue to Checkout]** está esmaecido.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.
