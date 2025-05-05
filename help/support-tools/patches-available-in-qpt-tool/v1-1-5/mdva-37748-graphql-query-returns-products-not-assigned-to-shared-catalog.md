---
title: 'MDVA-37748: a consulta do GraphQL retorna produtos não atribuídos ao catálogo compartilhado'
description: O patch MDVA-37748 corrige o problema em que uma consulta do GraphQL retorna produtos não atribuídos a um catálogo compartilhado. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.5 está instalada. A ID do patch é MDVA-37748. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.
exl-id: 1f441882-dc14-433c-aa03-ff22483ce5a7
feature: B2B, GraphQL, Catalog Management, Categories, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '498'
ht-degree: 0%

---

# MDVA-37748: a consulta do GraphQL retorna produtos não atribuídos ao catálogo compartilhado

O patch MDVA-37748 corrige o problema em que uma consulta do GraphQL retorna produtos não atribuídos a um catálogo compartilhado. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.5 está instalada. A ID do patch é MDVA-37748. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.4.2

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.4.2 - 2.4.2-p2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O query do GraphQL retorna produtos não atribuídos a um catálogo compartilhado.

<u>Pré-requisitos</u>:

Os módulos B2B são instalados.

<u>Etapas a serem reproduzidas</u>:

1. Crie dois produtos e atribua-os a uma categoria:
   * Product 1 - Public
   * Product 2

1. Atribua o &quot;Produto 1 - Público&quot; ao catálogo compartilhado &quot;Padrão (Geral)&quot;.
1. Crie um catálogo compartilhado personalizado adicional e atribua-o ao &quot;Produto 2&quot;.
1. Crie uma nova empresa e atribua-a ao catálogo compartilhado adicional criado na etapa três.
1. Após a execução/reindexação do cron, no front-end, valide se você pode ver &quot;Produto 1 - Público&quot; se não estiver conectado.
1. Faça logon como administrador da empresa criada na etapa quatro e confirme se você só vê o &quot;Produto 2&quot;.
1. Solicite um token de autorização usando a seguinte consulta do GraphQL:

   <pre>
    <code class="language-graphql">
    mutation &lbrace;
      generateCustomerToken(
        email: "company.admin@exapmle.test"
        password: "password"
      ) &lbrace;
        token
      &rbrace;
    &rbrace;
    </code>
    </pre>

1. Adicione o cabeçalho **Valor do token do portador da autorização** e execute a seguinte consulta do GraphQL:

   <pre>
    <code class="language-graphql">
    &lbrace;
      products(
          filter: {},
          pageSize: 100,
          currentPage: 1
          sort: {}
        ) &lbrace;
          total_count
          page_info &lbrace;
            page_size
            current_page
          &rbrace;
          aggregations &lbrace;
            attribute_code
            count
            label
            options &lbrace;
              label
              value
              count
            &rbrace;
          &rbrace;
          items &lbrace;
            name
            sku
            created_at
            updated_at
            stock_status
            description {html}
            short_description {html}
            url_key
            url_path
            price_tiers&lbrace;
              final_price&lbrace;
                  value
                  currency
                &rbrace;
              discount&lbrace;
                  amount_off
                  percent_off
                &rbrace;
              quantity
            &rbrace;
            price_range &lbrace;
             maximum_price &lbrace;
              regular_price &lbrace;
                value
              &rbrace;
              final_price &lbrace;
                value
              &rbrace;
            &rbrace;
            minimum_price &lbrace;
              regular_price &lbrace;
                value
              &rbrace;
              final_price &lbrace;
               value
              &rbrace;
            &rbrace;
          &rbrace;
          image &lbrace;
           url
          &rbrace;
          thumbnail &lbrace;
           url
          &rbrace;
          small_image &lbrace;
           url
          &rbrace;
          media_gallery &lbrace;
           url
          &rbrace;
          ... on ConfigurableProduct &lbrace;
            configurable_options &lbrace;
             id

             label
             position
             use_default
             attribute_code
             values &lbrace;
               value_index
               label
               swatch_data &lbrace;
                 value
               &rbrace;
            &rbrace;
            product_id
          &rbrace;
          variants &lbrace;
            product &lbrace;
              id
              name
              sku
              &#x200B;#margin
              &#x200B;#margin_percentage
              image &lbrace;
                url
              &rbrace;
              small_image &lbrace;
                url
              &rbrace;
              thumbnail &lbrace;
                url
              &rbrace;
              media_gallery&lbrace;
                url
              &rbrace;
              attribute_set_id
              ... on PhysicalProductInterface &lbrace;
                weight
              &rbrace;
              price_range &lbrace;
                minimum_price &lbrace;
                  regular_price &lbrace;
                    value
                    currency
                  &rbrace;
                &rbrace;
              &rbrace;
            &rbrace;
            attributes &lbrace;
              label
              code
              value_index
            &rbrace;
          &rbrace;
        &rbrace;
      &rbrace;

    &rbrace;
&rbrace;
</code>
</pre>

<u>Resultados esperados</u>:

A contagem e o produto retornado pela GraphQL consideram apenas o produto atribuído ao catálogo compartilhado associado ao usuário conectado.

<u>Resultados reais</u>:

Apenas &quot;Produto 2&quot; é retornado, mas `total_count` mostra dois.

<pre>
<code class="language-graphql">
&lbrace;
  "data": &lbrace;
    "products": &lbrace;
      "total_count": 2,
      "page_info": &lbrace;
        "page_size": 100,
        "current_page": 1
      &rbrace;,
      "aggregations": &lbrack;
        &lbrace;
          "attribute_code": "price",
          "count": 2,
          "label": "Price",
          "options": &lbrack;
            &lbrace;
              "label": "0-100",
              "value": "0_100",
              "count": 1
            &rbrace;,
            &lbrace;
              "label": "100-200",
              "value": "100_200",
              "count": 1
            &rbrace;
          &rbrack;
        &rbrace;,
        &lbrace;
          "attribute_code": "category_id",
          "count": 1,
          "label": "Category",
          "options": &lbrack;
            &lbrace;
              "label": "Cat 1",
              "value": "3",
              "count": 2
            &rbrace;
          &rbrack;
        &rbrace;
      &rbrack;,
      "items": &lbrack;
        &lbrace;
          "name": "Product 2",
          "sku": "Product 2",
          "created_at": "2021-05-12 10:51:44",
          "updated_at": "2021-05-12 11:03:24",
          "stock_status": "IN_STOCK",
          "description": &lbrace;
            "html": ""
          &rbrace;,
          "short_description": &lbrace;
            "html": ""
          &rbrace;,
          "url_key": "product-2",
          "url_path": null,
          "price_tiers": &lbrack;
            &lbrace;
              "final_price": &lbrace;
                "value": 90,
                "currency": "USD"
              &rbrace;,
              "discount": &lbrace;
                "amount_off": 10,
                "percent_off": 10
              &rbrace;,
              "quantity": 1
            &rbrace;
          &rbrack;,
          "price_range": &lbrace;
            "maximum_price": &lbrace;
              "regular_price": &lbrace;
                "value": 100
              &rbrace;,
              "final_price": &lbrace;
                "value": 90
              &rbrace;
            &rbrace;,
            "minimum_price": &lbrace;
              "regular_price": &lbrace;
                "value": 100
              &rbrace;,
              "final_price": &lbrace;
                "value": 90
              &rbrace;
            &rbrace;
          &rbrace;,
          "image": &lbrace;
            "url": "../pub/static/version1620816308/frontend/Magento/luma/en_US/Magento_Catalog/images/product/placeholder/image.jpg"
          &rbrace;,
          "thumbnail": &lbrace;
            "url": "../pub/static/version1620816308/frontend/Magento/luma/en_US/Magento_Catalog/images/product/placeholder/thumbnail.jpg"
          &rbrace;,
          "small_image": &lbrace;
            "url": "../pub/static/version1620816308/frontend/Magento/luma/en_US/Magento_Catalog/images/product/placeholder/small_image.jpg"
          &rbrace;,
          "media_gallery": []
        &rbrace;
      &rbrack;
    &rbrace;
  &rbrace;
&rbrace;
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

Para obter informações sobre outros patches disponíveis no QPT, consulte a seção [Patches disponíveis no QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).
