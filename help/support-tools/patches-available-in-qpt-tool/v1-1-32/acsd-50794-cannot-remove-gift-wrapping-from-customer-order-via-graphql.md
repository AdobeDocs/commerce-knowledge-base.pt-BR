---
title: 'ACSD-50794: não é possível remover invólucro do presente do pedido do cliente via GraphQL'
description: Aplique o patch ACSD-50794 para corrigir o problema do Adobe Commerce em que os usuários não podem remover a embalagem do presente do pedido do cliente por meio do GraphQL.
exl-id: 4983910c-9ea0-451e-a2b6-81485184bbce
feature: Gift, GraphQL, Orders
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 0%

---

# ACSD-50794: não é possível remover invólucro do presente do pedido do cliente via GraphQL

O patch ACSD-50794 corrige o problema em que os usuários não podem remover a embalagem do presente do pedido do cliente por meio do GraphQL. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.32 está instalado. A ID do patch é ACSD-50794. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.1 - 2.4.6-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os usuários não podem remover a embalagem do presente do pedido do cliente por meio do GraphQL.

<u>Etapas a serem reproduzidas</u>:

1. Crie um cliente a partir do front-end.
1. Crie um produto simples.
1. Habilite *[!UICONTROL Gift Messages]* indo até **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Gift Options]** e defina *[!UICONTROL Allow Gift Messages]* = *[!UICONTROL Yes]*.
1. Crie *[!UICONTROL Gift Wrapping]* indo para **[!UICONTROL Stores]** > **[!UICONTROL Other Settings]** > **[!UICONTROL Gift Wrapping]**.
1. Obtenha o token do cliente.
1. Crie um carrinho vazio, customerCart.
   * Adicionar produtos ao carrinho: `addProductsToCart` mutação
   * Definir endereço de cobrança: `setBillingAddressOnCart` mutação
   * Definir endereço de entrega: `setShippingAddressesOnCart` mutação
   * Definir método de envio: `setShippingMethodsOnCart` mutação (taxa plana)
   * Definir método de pagamento: `setPaymentMethodOnCart` mutação (checkmo)
1. Agora verifique o invólucro do presente *Uid* com esta consulta de carrinho:

   <pre><code class="language-GraphQL">
    &lbrace;
      cart(cart_id: "{{CART_ID}}") &lbrace;
        available_gift_wrappings&lbrace;
            uid
        &rbrace;
    &rbrace;
    &rbrace;
    </code></pre>

1. Definir invólucro do presente usando `setGiftOptionsOnCart`.
1. Verifique o carrinho: cart query.
1. Desfazer a definição do invólucro do presente usando `setGiftOptionsOnCart` (defina o valor como nulo).
1. Novamente, verifique o carrinho: cart query.
1. Ordem de colocação: `placeOrder` mutação.
1. Executar consulta de cliente: cliente.

   <pre><code class="language-graphql">
    query &lbrace;
      customer &lbrace;
        firstname
        middlename
        lastname
        suffix
        email
        orders &lbrace;
            items &lbrace;
                order_date
                gift_wrapping &lbrace;
                    design
                    uid
                &rbrace;
            &rbrace;
        &rbrace;
        addresses &lbrace;
          firstname
          middlename
          lastname
          street
          city
          region &lbrace;
            region_code
            region
          &rbrace;
          postcode
          country_code
          telephone
        &rbrace;
      &rbrace;
    &rbrace;
    </code></pre>

<u>Resultados esperados</u>:

Depois que um usuário define um invólucro de presente e o cancela, a consulta do cliente retorna nulo.

<u>Resultados reais</u>:

A consulta do cliente ainda retorna o invólucro do presente conforme aplicado.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] versão: uma nova ferramenta para autoatender patches de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando o [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
