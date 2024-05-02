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

O patch ACSD-51305 corrige o problema em que os produtos derivados compostos esgotados não estão disponíveis na resposta do GraphQL. Este patch está disponível quando a variável [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.32 está instalado. A ID do patch é ACSD-51305. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6 - 2.4.6-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os produtos derivados compostos indisponíveis não estão disponíveis na resposta da GraphQL.

<u>Etapas a serem reproduzidas</u>:

1. Faça logon no site de administração.
1. Crie uma categoria (cat1, id=3).
1. Criar um *simple1* produto (esgotado, não visível individualmente, atribuído a *cat1*).
1. Criar um *simple2* produto (em estoque, não visível individualmente, atribuído a *cat1*).
1. Criar um *pacote1* produto com *simple1* e *simple2* produtos derivados como botão de opção *option1* produtos e atribua-o à *cat1* categoria.
1. Ir para **[!UICONTROL Admin]** > **[!UICONTROL System]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]**.

   * Definir **[!UICONTROL Display Out of Stock Products]** para *Sim*.

1. Abra o *pacote1* produto na loja e garantir que ambos *simple1* e *simple2* produtos secundários são exibidos dentro dele.
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

A variável **[!UICONTROL Product]** seção dentro do **[!UICONTROL Options]** bloco não está vazio.

<u>Resultados reais</u>:

A variável **[!UICONTROL Product]** seção dentro do **[!UICONTROL Options]** bloco está vazio.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.
