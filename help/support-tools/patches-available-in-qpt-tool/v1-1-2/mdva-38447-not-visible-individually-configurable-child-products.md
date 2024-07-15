---
title: 'MDVA-38447: produtos filho configuráveis "Não visíveis individualmente" são retornados na resposta do GraphQL e a consulta do MySQL é lenta'
description: O patch do Adobe Commerce MDVA-38447 corrige o problema em que os produtos secundários configuráveis "Não visíveis individualmente" são retornados na resposta do GraphQL e a consulta MySQL lenta para consulta de produtos GraphQL com filtro de categoria. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2 está instalada. A ID do patch é MDVA-38447. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.
exl-id: 302e7458-d9ea-466a-a2ac-d86a8ee3eca3
feature: B2B, GraphQL, Categories, Configuration, Products, Services
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
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
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

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
) {
  products(
    filtro: $filter
    sort: $sort
    pesquisa: $search
    pageSize: $pageSize
    currentPage: $currentPage
  ) {
    total_count
    page_info {
      total_páginas
      current_page
      page_size
    }
    itens {
      name
      sku
    }
  }
}</pre>

Variáveis:

<pre>{"filter":{"user_group":{"eq":"}},"search":"config-100","sort":{},"pageSize":200,"currentPage":1}
</pre>

<u>Resultados esperados</u>:

Os produtos com visibilidade definida como &quot;Não visível individualmente&quot; não serão retornados em resposta.

<u>Resultados reais</u>:

Os produtos com visibilidade definida como &quot;Não visível individualmente&quot; são retornados em resposta.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do tipo de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre correções de qualidade para o Adobe Commerce, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Para obter informações sobre outros patches disponíveis no QPT, consulte a seção [Patches disponíveis no QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).
