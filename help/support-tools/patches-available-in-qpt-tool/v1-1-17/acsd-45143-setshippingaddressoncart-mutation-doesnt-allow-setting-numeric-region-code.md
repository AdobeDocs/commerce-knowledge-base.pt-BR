---
title: 'ACSD-45143: a mutação setShippingAddressesOnCart não define o código de região numérica como "região"'
description: O patch ACSD-45143 corrige o problema em que a mutação setShippingAddressesOnCart não permite definir o código de região numérica como "região". Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.17 está instalada. A ID do patch é ACSD-45143. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.
exl-id: 5867ea97-7d54-486e-b5d0-bfb87f24fb80
feature: Orders, Shipping/Delivery, Shopping Cart
role: Admin
source-git-commit: 8b6bf1cdada7edb0cdb0bb3e90ed15ee8cebf77e
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# ACSD-45143: a mutação setShippingAddressesOnCart não define o código de região numérica como &quot;região&quot;

O patch ACSD-45143 corrige o problema em que a mutação setShippingAddressesOnCart não permite definir o código de região numérica como &quot;região&quot;. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.17 está instalada. A ID do patch é ACSD-45143. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.0 - 2.4.4

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A mutação setShippingAddressesOnCart não permite definir o código de região numérico como &quot;região&quot;.

<u>Etapas a serem reproduzidas</u>:

1. Crie um carrinho usando a consulta abaixo.

   <pre>
    <code class="language-graphql">
    mutation {
      createEmptyCart
    }
    </code>
    </pre>

1. Envie uma solicitação para definir o endereço de entrega do carrinho.

   <pre>
    <code class="language-graphql">
    mutation ($cartId: String!) {
      setShippingAddressesOnCart(
        input: {
          cart_id: $cartId
          shipping_addresses: {
            address: {
              firstname: "Tomek"
              lastname: "Nowak"
              company: "Company Name"
              street: ["234 Rue de Rivoli"]
              region: "58"
              city: "Lille"
              postcode: "59800"
              country_code: "FR"
              telephone: "123-456-0000"
              save_in_address_book: false
            }
          }
        }
        ) {
          cart {
            shipping_addresses {
              firstname
              lastname
              company
              street
              city
              region {
                code
                label
              }
              postcode
              telephone
              country {
                code
                label
              }
            }
          }
        }
      }
      </code>
      </pre>

   Observação: neste exemplo, o código do país é definido como &quot;FR&quot; e o código da região como &quot;58&quot;. De acordo com a tabela Db `directory_country_region`, o código de região 58 é &quot;Nièvre&quot;.

1. Verifique a resposta retornada.

<u>Resultados esperados</u>:

O Adobe Commerce permite definir o código de região numérica na solicitação do GraphQL.

<u>Resultados reais</u>:

O código de região é alterado para 47.

<pre>
<code class="language-graphql">
{
  "data": {
    "setShippingAddressesOnCart": {
      "cart": {
        "shipping_addresses": [
        {
          "firstname": "Tomek",
          "lastname": "Nowak",
          "company": "Company Name",
          "street": [
          "234 Rue de Rivoli"
          ],
          "city": "Lille",
          "region": {
            "code": "47",
            "label": "Lot-et-Garonne"
            },
            "postcode": "59800",
            "telephone": "123-456-0000",
            "country": {
              "code": "FR",
              "label": "FR"
            }
          }
        ]
      }
    }
  }
}
</code>
</pre>

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) na documentação do desenvolvedor.
