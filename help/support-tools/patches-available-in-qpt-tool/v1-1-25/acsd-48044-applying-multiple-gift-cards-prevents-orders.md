---
title: "ACSD-48044: a aplicação de vários cartões-presente impede que os pedidos sejam feitos"
description: Aplique o patch ACSD-48044 para corrigir o problema do Adobe Commerce, onde a aplicação de vários cartões-presente a um único pedido com vários envios impede que os pedidos sejam feitos.
exl-id: fe57063c-d69c-4b80-a59c-912c2603f6af
feature: Admin Workspace, Gift, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '486'
ht-degree: 0%

---

# ACSD-48044: a aplicação de vários cartões-presente impede que os pedidos sejam feitos

O patch ACSD-48044 corrige o problema em que a aplicação de vários cartões-presente a um único pedido com vários envios impede que os pedidos sejam feitos. Este patch está disponível quando a variável [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.25 está instalado. A ID do patch é ACSD-48044. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.4 - 2.4.5-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Aplicar vários cartões-presente a um único pedido com remessa múltipla impede que os pedidos sejam feitos.

<u>Etapas a serem reproduzidas</u>:

1. Instale uma versão limpa do Adobe Commerce.
1. Crie um produto simples com um preço de $100 e outro produto simples com um preço de $10.
1. Faça logon no [!UICONTROL Admin panel] e crie dois cartões-presente.

   * 02KB8M0H0GRD = US$ 50
   * 00GXM6SUGBLW = US$ 25

1. Crie um cliente com dois endereços.
1. Adicione dois produtos ao carrinho.

   * Adicione o produto de US$ 10 primeiro e, em seguida, adicione o produto de US$ 100. O problema não pode ser reproduzido se o produto de US$ 100 for adicionado primeiro.

1. Vá para o carrinho de compras e adicione os dois cartões-presente que você criou.
1. Clique em **[!UICONTROL Ship to Multiple Addresses]** na página do carrinho.
1. Atribua cada produto a um endereço diferente.
1. Vá para a **[!UICONTROL Shipping information]** página.
1. Vá para a **[!UICONTROL Billing information]** página.
1. Vá para a **[!UICONTROL Review Your Order]** página, onde você pode ver o problema.
1. Tente fazer o pedido.

<u>Resultados esperados</u>:

* Os cartões-presente são aplicados corretamente ao valor total.
* Os pedidos são feitos.

<u>Resultados reais</u>:

Os valores do cartão-presente estão misturados com um erro *&quot;Corrija o código do cartão-presente.&quot;* ao fazer o pedido.

* Primeiro produto:

   * Remover Cartão Presente (00GXM6SUGBLW) - $15,00
   * Remover Cartão Presente (02KB8M0H0GRD) - $0,00

* Segundo produto:

   * Remover Cartão Presente (00GXM6SUGBLW) - $25,00
   * Remover Cartão Presente (02KB8M0H0GRD) - $35,00

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.
