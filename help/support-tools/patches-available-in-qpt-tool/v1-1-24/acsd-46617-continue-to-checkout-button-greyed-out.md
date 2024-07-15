---
title: 'ACSD-46617: **[!UICONTROL Continue to Checkout]** botão esmaecido quando o subtotal é maior que o valor mínimo de pedido configurado'
description: Aplique o patch ACSD-46617 para resolver o problema do Adobe Commerce em que o botão **[!UICONTROL Continue to Checkout]** fica esmaecido mesmo se o subtotal for maior que a quantidade mínima de pedido configurada.
exl-id: 42fe02bd-f48b-4c6d-8643-ea2c1aa98c94
feature: Checkout, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---

# ACSD-46617: botão &quot;[!UICONTROL Continue to Checkout]&quot; esmaecido quando um subtotal maior que &quot;[!UICONTROL Minimum Order Amount]&quot;

Este patch ACSD-46617 resolve o problema em que o botão **[!UICONTROL Continue to Checkout]** fica esmaecido mesmo se o subtotal for maior que o valor mínimo de pedido configurado. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.24 está instalado. A ID do patch é ACSD-46617. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O botão **[!UICONTROL Continue to Checkout]** ficará esmaecido mesmo se o subtotal for maior que o valor mínimo de pedido configurado.

<u>Etapas a serem reproduzidas</u>:

1. Vá para Adobe Commerce Admin > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Minimum Order Amount]** e defina o seguinte:
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
1. Vá para o carrinho de compras, selecione o método $5 **[!UICONTROL Flat Rate shipping]** e aplique o código do cupom.
1. Acesse o check-out, conclua o envio e navegue até a seção **[!UICONTROL Paytment]**.
1. Volte para o carrinho de compras.

<u>Resultados esperados</u>:

Não há erro relacionado ao valor mínimo do pedido, pois o total geral de US$ 2,4 é maior que o valor necessário de US$ 2.

<u>Resultados reais</u>:

* Há um erro relacionado ao valor mínimo do pedido mesmo quando o total geral de US$ 2,4 é maior que o valor mínimo do pedido de US$ 2.
* O botão **[!UICONTROL Continue to Checkout]** está esmaecido.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] versão: uma nova ferramenta para autoatender patches de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando o [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
