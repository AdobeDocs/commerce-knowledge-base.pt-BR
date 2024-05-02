---
title: "ACSD-50794: não é possível remover invólucro do presente do pedido do cliente via GraphQL"
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

O patch ACSD-50794 corrige o problema em que os usuários não podem remover a embalagem do presente do pedido do cliente por meio do GraphQL. Este patch está disponível quando a variável [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.32 está instalado. A ID do patch é ACSD-50794. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.1 - 2.4.6-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os usuários não podem remover a embalagem do presente do pedido do cliente por meio do GraphQL.

<u>Etapas a serem reproduzidas</u>:

1. Crie um cliente a partir do front-end.
1. Crie um produto simples.
1. Ativar *[!UICONTROL Gift Messages]* acessando **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Gift Options]** e defina *[!UICONTROL Allow Gift Messages]* = *[!UICONTROL Yes]*.
1. Criar *[!UICONTROL Gift Wrapping]* acessando **[!UICONTROL Stores]** > **[!UICONTROL Other Settings]** > **[!UICONTROL Gift Wrapping]**.
1. Obtenha o token do cliente.
1. Crie um carrinho vazio, customerCart.
   * Adicionar produtos ao carrinho: `addProductsToCart` mutação
   * Definir endereço de cobrança: `setBillingAddressOnCart` mutação
   * Definir endereço de entrega: `setShippingAddressesOnCart` mutação
   * Definir método de envio: `setShippingMethodsOnCart` mutação (flatrate)
   * Definir método de pagamento: `setPaymentMethodOnCart` mutação (checkmo)
1. Agora verifique a embalagem do presente *Uid* com esta consulta ao carrinho:

   <pre><code class="language-GraphQL">
    {
      cart(cart_id: "{{CART_ID}}") {
        available_gift_wrappings{
            uid
        }
    }
    }
    </code></pre>

1. Definir invólucro do presente usando `setGiftOptionsOnCart`.
1. Verifique o carrinho: cart query.
1. Não definir invólucro do presente usando `setGiftOptionsOnCart` (defina o valor como nulo).
1. Novamente, verifique o carrinho: cart query.
1. Fazer pedido: `placeOrder` mutação.
1. Executar consulta de cliente: cliente.

   <pre><code class="language-graphql">
    query {
      customer {
        firstname
        middlename
        lastname
        suffix
        email
        orders {
            items {
                order_date
                gift_wrapping {
                    design
                    uid
                }
            }
        }
        addresses {
          firstname
          middlename
          lastname
          street
          city
          region {
            region_code
            region
          }
          postcode
          country_code
          telephone
        }
      }
    }
    </code></pre>

<u>Resultados esperados</u>:

Depois que um usuário define um invólucro de presente e o cancela, a consulta do cliente retorna nulo.

<u>Resultados reais</u>:

A consulta do cliente ainda retorna o invólucro do presente conforme aplicado.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.
