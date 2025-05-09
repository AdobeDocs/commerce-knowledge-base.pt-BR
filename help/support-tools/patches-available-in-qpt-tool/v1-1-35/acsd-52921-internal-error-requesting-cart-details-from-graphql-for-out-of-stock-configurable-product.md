---
title: 'ACSD-52921: erro ao solicitar detalhes do carrinho da GraphQL para produto configurável indisponível'
description: Aplique o patch ACSD-52921 para corrigir o problema do Adobe Commerce em que ocorre um erro interno ao solicitar detalhes do carrinho da GraphQL para um produto configurável indisponível.
feature: GraphQL, Configuration, Products, Shopping Cart
role: Admin
exl-id: 687460c4-f0d5-45d2-82b1-dda2947fe1e7
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# ACSD-52921: erro ao solicitar detalhes do carrinho da GraphQL para produto configurável indisponível

O patch ACSD-52921 corrige o problema em que ocorre um erro interno ao solicitar detalhes do carrinho da GraphQL para um produto configurável indisponível. Este patch está disponível quando o [!DNL Quality Patches Tool (QPT)] 1.1.35 está instalado. A ID do patch é ACSD-52921. Observe que o problema foi corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Ocorre um erro interno ao solicitar detalhes do carrinho da GraphQL para um produto configurável indisponível.

<u>Etapas a serem reproduzidas</u>:

1. Crie um produto configurável com algumas opções.
1. Adicione uma opção do produto configurável acima ao carrinho a partir do front-end (check-out do convidado).
1. Obtenha o `[ masked_id ]` da tabela do banco de dados `[ quote_id_mask ]` para a cotação criada acima.
1. Execute a seguinte consulta do GraphQL para obter os detalhes do carrinho de convidado acima.

   Adicione o `[ masked_id ]` recebido da etapa 3 na consulta.

   ```GraphQL
   {
       cart(cart_id: "masked_id") {
           items {
               product {
                   name
                   sku
               }
               ... on ConfigurableCartItem {
                   configurable_options {
                       configurable_product_option_uid
                       option_label
                       configurable_product_option_value_uid
                       value_label
                   }
               }
               quantity
               errors {
                   code
                   message
               }
           }
       }
   }   
   ```

1. Isso retornará os detalhes da cotação sem problemas.
1. Vá para o back-end e atualize os produtos configuráveis *[!UICONTROL Stock Status]* para *[!UICONTROL Out of Stock]*.
1. Execute a mesma consulta do GraphQL, como feito na etapa 4.

<u>Resultados esperados</u>:

A mensagem de erro é enviada/tratada corretamente na resposta.

<u>Resultados reais</u>:

Erro do *500 Internal Server* lançado em resposta à consulta do GraphQL.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] versão: uma nova ferramenta para autoatender patches de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando o [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
