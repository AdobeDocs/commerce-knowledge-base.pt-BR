---
title: 'MDVA-38447: os produtos secundários configuráveis "Não visíveis individualmente" são retornados na resposta do GraphQL e a consulta do MySQL é lenta'
description: O patch do Adobe Commerce MDVA-38447 corrige o problema em que os produtos secundários configuráveis "Não visíveis individualmente" são retornados na resposta do GraphQL e a consulta MySQL lenta para consulta de produtos GraphQL com filtro de categoria. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2 está instalada. A ID do patch é MDVA-38447. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.
exl-id: 302e7458-d9ea-466a-a2ac-d86a8ee3eca3
feature: B2B, GraphQL, Categories, Configuration, Products, Services
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '487'
ht-degree: 0%

---

# MDVA-38447: os produtos secundários configuráveis &quot;Não visíveis individualmente&quot; são retornados na resposta do GraphQL e a consulta do MySQL é lenta

O patch do Adobe Commerce MDVA-38447 corrige o problema em que os produtos secundários configuráveis &quot;Não visíveis individualmente&quot; são retornados na resposta do GraphQL e a consulta MySQL lenta para consulta de produtos GraphQL com filtro de categoria. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2 está instalada. A ID do patch é MDVA-38447. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2 - 2.4.3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os produtos secundários configuráveis &quot;Não visíveis individualmente&quot; são retornados na resposta do GraphQL e na consulta lenta do MySQL para produtos da GraphQL com filtro de categoria.

<u>Pré-requisitos</u>:

Os módulos B2B devem ser instalados.

<u>Etapas a serem reproduzidas</u>:

1. Crie um produto configurável com produtos simples definidos como **Não visíveis individualmente**.
1. Executar uma **reindexação completa**.
1. Executar uma **consulta do GraphQL** como:

<pre>consulta getFilteredProducts(
  $filter: ProductAttributeFilterInput!
  $sort: ProductAttributeSortInput!
  $search: String
  $pageSize: Int!
  $currentPage: Int!
) &lbrace;
  products(
    filtro: $filter
    sort: $sort
    pesquisa: $search
    pageSize: $pageSize
    currentPage: $currentPage
  ) &lbrace;
    total_count
    page_info &lbrace;
      total_páginas
      current_page
      page_size
    &rbrace;
    itens &lbrace;
      name
      sku
    &rbrace;
  &rbrace;
&rbrace;</pre>

Variáveis:

<pre>{"filter":{"user_group":{"eq":"}},"search":"config-100","sort":{},"pageSize":200,"currentPage":1}
</pre>

<u>Resultados esperados</u>:

Os produtos com visibilidade definida como &quot;Não visível individualmente&quot; não serão retornados em resposta.

<u>Resultados reais</u>:

Os produtos com visibilidade definida como &quot;Não visível individualmente&quot; são retornados em resposta.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do tipo de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/usage) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/pt-br/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre correções de qualidade para o Adobe Commerce, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Para obter informações sobre outros patches disponíveis no QPT, consulte a seção [Patches disponíveis no QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).
