---
title: "ACSD-51305: produtos filho compostos indisponíveis no estoque na resposta do GraphQL"
description: Aplique o patch ACSD-51305 para corrigir o problema do Adobe Commerce em que os produtos derivados compostos indisponíveis não estão disponíveis na resposta do GraphQL.
exl-id: 0f33eb62-dfd3-4d07-b095-9ee6e9983c4d
feature: Categories, GraphQL, Orders, Products
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 0%

---

# ACSD-51305: produtos filho compostos indisponíveis no estoque na resposta do GraphQL

O patch ACSD-51305 corrige o problema em que os produtos derivados compostos esgotados não estão disponíveis na resposta do GraphQL. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.32 está instalado. A ID do patch é ACSD-51305. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6 - 2.4.6-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os produtos derivados compostos indisponíveis não estão disponíveis na resposta da GraphQL.

<u>Etapas a serem reproduzidas</u>:

1. Faça logon no site de administração.
1. Crie uma categoria (cat1, id=3).
1. Crie um produto *simple1* (esgotado, não visível individualmente, atribuído a *cat1*).
1. Crie um produto *simple2* (no estoque, não visível individualmente, atribuído a *cat1*).
1. Crie um produto *bundle1* com produtos filho *simple1* e *simple2* como produtos de botão de opção *option1* e atribua-o à categoria *cat1*.
1. Vá para **[!UICONTROL Admin]** > **[!UICONTROL System]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]**.

   * Defina **[!UICONTROL Display Out of Stock Products]** como *Sim*.

1. Abra o produto *bundle1* na vitrine e verifique se os produtos filho do *simple1* e do *simple2* são exibidos dentro dele.
1. Execute a seguinte consulta do GraphQL:

   ```GraphQL
   {
       categoryList(filters: { ids: { in: ["3"] } }) {
           id
           name
           products(pageSize: 8, sort: { position: ASC }) {
               total_count
               items {
                   id
                   sku
                   name
                   ... on BundleProduct {
                       url_key
                       items {
                           title
                           sku
                           options {
                               quantity
                               position
                               is_default
                               product {
                                   id
                                   name
                                   sku
                               }
                           }
                       }
                   }
               }
           }
       }
   }
   ```

<u>Resultados esperados</u>:

A seção **[!UICONTROL Product]** dentro do bloco **[!UICONTROL Options]** não está vazia.

<u>Resultados reais</u>:

A seção **[!UICONTROL Product]** dentro do bloco **[!UICONTROL Options]** está vazia.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] versão: uma nova ferramenta para autoatender patches de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando o [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
