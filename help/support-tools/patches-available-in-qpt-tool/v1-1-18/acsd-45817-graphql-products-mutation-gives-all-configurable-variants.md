---
title: "ACSD-45817: a mutação de produtos GraphQL fornece todas as variantes configuráveis"
description: O patch ACSD-45817 corrige o problema em que uma mutação "products" do GraphQL para uma loja específica retorna todas as variantes configuráveis, incluindo aquelas não atribuídas à loja solicitada. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.18 está instalada. A ID do patch é ACSD-45817. Observe que o problema foi corrigido no Adobe Commerce 2.4.4.
exl-id: 3d61d1aa-36b5-471d-929b-7df8ce65c791
feature: GraphQL, Configuration, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 0%

---

# ACSD-45817: a mutação de produtos GraphQL fornece todas as variantes configuráveis

O patch ACSD-45817 corrige o problema em que um GraphQL `products` mutação para um armazenamento específico retorna todas as variantes configuráveis, incluindo aquelas não atribuídas ao armazenamento solicitado. Este patch está disponível quando a variável [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.18 está instalado. A ID do patch é ACSD-45817. Observe que o problema foi corrigido no Adobe Commerce 2.4.4.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2 - 2.4.3-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A GRAPHQL `products` mutação para um armazenamento específico retorna todas as variantes configuráveis, incluindo aquelas não atribuídas ao armazenamento solicitado.

<u>Pré-requisitos</u>:

Crie um segundo site, uma segunda loja e uma visualização de segunda loja.

<u>Etapas a serem reproduzidas</u>:

1. Crie um produto configurável com dois subprodutos: &quot;configurable-a&quot; e &quot;configurable-b&quot;.
1. Atribua o produto configurável a ambos os sites.
1. Atribua apenas uma variação &quot;configurável-a&quot; ao segundo site.
1. Vá para a **Loja**, alterne para o 2º site e abra o produto configurável.
1. Verifique se você vê apenas uma opção secundária: &quot;configurable-a&quot;.
1. Execute uma consulta do GraphQL usando `POST: /graphql` endpoint e `Headers: "store" = "new"`

   ```GraphQL
   {
     products(filter: { sku: { eq: "configurable" } }) {
       items {
         id
         attribute_set_id
         name
         sku
         __typename
         price_range{
           minimum_price{
             regular_price{
               value
               currency
             }
           }
         }
         categories {
           id
         }
         ... on ConfigurableProduct {
           configurable_options {
             id
             attribute_id_v2
             label
             position
             use_default
             attribute_code
             values {
               value_index
               label
             }
             product_id
           }
           variants {
             product {
               id
               name
               sku
               attribute_set_id
               ... on PhysicalProductInterface {
                 weight
               }
               price_range{
                 minimum_price{
                   regular_price{
                     value
                     currency
                   }
                 }
               }
             }
             attributes {
               uid
               label
               code
               value_index
             }
           }
         }
       }
     }
   }
   ```

<u>Resultados esperados</u>:

A variação &quot;configurable-b&quot; não é atribuída ao segundo site e não deve ser exibida na resposta.

<u>Resultados reais</u>:

A variação &quot;configurable-b&quot; é exibida na resposta.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de atualização de software > Aplicar patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatendimento de correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de patches de qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.
