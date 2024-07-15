---
title: "MDVA-36170: a consulta do GraphQL à categoria retorna dados não armazenados em cache"
description: O patch MDVA-36170 corrige o problema em que o resultado da consulta do GraphQL não é armazenado em cache. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20 está instalada. A ID do patch é MDVA-36170. Observe que o problema foi corrigido no Adobe Commerce 2.4.2.
exl-id: 6249b751-4b71-4833-ab86-ded615d648a8
feature: Cache, GraphQL, Categories
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# MDVA-36170: a consulta do GraphQL à categoria retorna dados não armazenados em cache

O patch MDVA-36170 corrige o problema em que o resultado da consulta do GraphQL não é armazenado em cache. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20 está instalada. A ID do patch é MDVA-36170. Observe que o problema foi corrigido no Adobe Commerce 2.4.2.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

Adobe Commerce na infraestrutura em nuvem 2.3.6

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.3.1 - 2.4.1-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Corrige o problema em que o resultado da consulta do GraphQL não é armazenado em cache.

<u>Etapas a serem reproduzidas</u>:

O comerciante está usando o método GET para armazenamento em cache do GraphQL, mas não está obtendo os dados em cache.

<pre>https://magento_url/graphql?query={ products(filtro: {category_id: {eq: "2"}}, pageSize: 2000, currentPage: 1, sort: {position: ASC}) {
itens {
  sku
  id
  name
  descrição {
    html
  }
  url_key
  especificações
  imagem {
    rótulo
    gallery_url
  }
  __typename
  quantity_in
  small_image {
    gallery_url
    rótulo
  }
  product_price_range {
    maximum_price {
      preço_final {
        value
      }
    }
    minimum_price {
      preço_final {
        value
      }
    }
  }
  ... no ConfigurableProduct {
    variantes{
      atributos{
        código
        rótulo
        value_index
      }
      produto{
        sku
        quantity_in
      }
    }
   }
  }
}
}}</pre>

<u>Resultados esperados</u>:

Os dados são armazenados em cache.

<u>Resultados reais</u>:

Os dados não são armazenados em cache.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.
