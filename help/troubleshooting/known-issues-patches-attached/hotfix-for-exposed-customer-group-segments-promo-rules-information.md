---
title: Nomes de grupos de clientes, segmentos e informações de regras promocionais expostos via  [!DNL GraphQL]
description: Este artigo fornece um hotfix para evitar a exposição de nomes de grupos de clientes, segmentos de clientes e informações de regras promocionais via  [!DNL GraphQL].
feature: GraphQL
role: Admin, Developer
source-git-commit: f32085c80c9dbce513dad15ebf5f77a0e6398466
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---


# Nomes de grupos de clientes, segmentos e informações de regras promocionais expostos via [!DNL GraphQL]

Este artigo fornece um hotfix para evitar a exposição de nomes de grupos de clientes, segmentos de clientes e informações de regras promocionais via [!DNL GraphQL]. O problema está programado para ser corrigido no Adobe Commerce 2.4.8-p1.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.8

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.8

## Problema

Para [!UICONTROL Storefront Personalization Drop-ins], novas mutações de [!DNL GraphQL] foram introduzidas para exibir informações básicas, como nomes de grupos de clientes, segmentos, carrinho e regras de catálogo. No entanto, isso pode expor dados confidenciais, como detalhes da oferta ou códigos de cupom, se incluídos nos nomes.

### Etapas a serem reproduzidas

#### Caso I: [!UICONTROL Catalog Rule]

1. Na barra lateral *Admin*, vá para **[!UICONTROL Marketing]** > **[!UICONTROL Catalog Price Rule]** > **[!UICONTROL Add New Rule]**.
1. Defina as condições da regra (por exemplo, atributo ou categoria do produto).
1. Salve e aplique a regra.
1. Certifique-se de que um produto atenda às condições da regra.
1. Execute a seguinte consulta [!DNL GraphQL] para buscar todas as regras:

   ```
   query {
       allCatalogRules {
           name
       }
   }
   ```

1. Consulte um produto para verificar se a regra se aplica:

   ```
   query {
       products(filter: { sku: { eq: "product-sku" } }) {
           items {
               name
               rules {
                   name
               }
           }
       }
   }
   ```

#### Caso II: [!UICONTROL Cart Rule]

1. Na barra lateral *Admin*, vá para **[!UICONTROL Marketing]** > **[!UICONTROL Cart Price Rule]** > **[!UICONTROL Add New Rule]**.
1. Defina condições como valor mínimo do carrinho e grupo de clientes.
1. Salve e aplique a regra.
1. Adicione produtos ao carrinho para acionar a regra.
1. Use [!DNL GraphQL] para verificar todas as regras do carrinho:

   ```
   query {
       allCartRules {
           name
       }
   }
   ```

1. Verifique se as regras são aplicadas ao carrinho ativo:

   ```
   query {
       cart(cart_id: "your-cart-id") {
           rules {
               name
           }
       }
   }
   ```

#### Caso III: [!UICONTROL Customer Group]

1. Na barra lateral *Admin*, vá para **[!UICONTROL Customers]** > **[!UICONTROL Customer Groups]**.
1. Verifique se os grupos esperados existem.
1. Usar [!DNL GraphQL] para buscar todos os grupos:

   ```
   query {
       allCustomerGroups {
           name
       }
   }
   ```

1. Verifique o grupo do cliente/convidado:

   ```
   query {
       customerGroup {
           name
       }
   }
   ```

#### Caso IV: [!UICONTROL Customer Segment] (somente para Adobe Commerce)

1. Na barra lateral *Admin*, vá para **[!UICONTROL Customers]** > **[!UICONTROL Customer Segments]** → **[!UICONTROL Add Segment]**.
1. Definir condições com base no cliente (por exemplo, pedido, conteúdo do carrinho).
1. Atribuir escopo aplicável: *[!UICONTROL Visitor]*, *[!UICONTROL Registered]* ou ambos.
1. Verifique se as condições correspondem a um cliente de teste.
1. Use [!DNL GraphQL] para verificar todos os segmentos:

   ```
   query {
       allCustomerSegments {
           name
           apply_to
       }
   }
   ```

1. Valide os segmentos aplicados a um carrinho:

   ```
   query {
       customerSegments(cartId: "your-cart-id") {
           name
       }
   }
   ```

<u>Resultado esperado</u>:

Os nomes de grupos de clientes, segmentos e informações de regras promocionais não são expostos por meio do [!DNL GraphQL].

<u>Resultado real</u>:

Nomes de grupos de clientes, segmentos e informações de regras promocionais são expostos por meio do [!DNL GraphQL].

## Solução

Aplique os patches anexados dependendo da sua versão do Adobe Commerce:

* Para a versão 2.4.8 do Adobe Commerce:

   * [LYNX-839_CE_2.4.8.patch](assets/LYNX-839_CE_2.4.8.patch.zip)
   * [LYNX-839_EE_2.4.8.patch](assets/LYNX-839_EE_2.4.8.patch.zip)

* Para [!DNL Magento], abra a versão 2.4.8 do Source:

   * [LYNX-839_CE_2.4.8.patch](assets/LYNX-839_CE_2.4.8.patch.zip)
