---
title: "MDVA-37362: as opções de produto configuráveis estão vazias na resposta do GraphQL"
description: O patch MDVA-37362 resolve o problema em que os valores configuráveis da opção do produto e os valores do atributo de variante estão vazios na resposta do GraphQL. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) v.1.0.23 está instalada. Observe que o problema está programado para ser corrigido no Adobe Commerce versão 2.4.3.
exl-id: a56db5e3-0841-4764-b430-d5775ebd1fe6
feature: GraphQL, Configuration, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# MDVA-37362: as opções de produto configuráveis estão vazias na resposta do GraphQL

O patch MDVA-37362 resolve o problema em que os valores configuráveis da opção do produto e os valores do atributo de variante estão vazios na resposta do GraphQL. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) v.1.0.23 está instalada. Observe que o problema está programado para ser corrigido no Adobe Commerce versão 2.4.3.

## Produtos e versões afetados

* O patch foi projetado para Adobe Commerce na infraestrutura em nuvem 2.4.2
* O patch também é compatível com o Adobe Commerce no local e o Adobe Commerce na infraestrutura em nuvem 2.3.4 - 2.4.2-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

<u>Etapas a serem reproduzidas:</u>

1. Crie uma nova fonte e um novo estoque atribuído a esta nova fonte.
1. **Lojas** > *Configurações* > **Configuração** > **Catálogo** > **Inventário** > *Opções de Estoque de Produtos* > Gerenciar Estoque: *SIM*.
1. Crie um produto configurável e atribua a quantidade do produto ao novo estoque criado na etapa 1.
1. Reindexar.
1. Faça uma solicitação do GraphQL.
1. Solicitação:

```java
{
  products(filter: { sku: { eq: "test-config-product" } }) {
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

<u>Resultados esperados:</u>

Valores e atributos de opção devem estar presentes na resposta.

<u>Resultados reais:</u>

```java
{
  "data": {
    "products": {
      "items": [
        {
          "id": 2048,
          "attribute_set_id": 4,
          "name": "Test Configurable Product",
          "sku": "test-config-product",
          "__typename": "ConfigurableProduct",
          "price_range": {
            "minimum_price": {
              "regular_price": {
                "value": 100,
                "currency": "USD"
              }
            }
          },
          "categories": [
            {
              "id": 3
            }
          ],
          "configurable_options": [
            {
              "id": 296,
              "attribute_id_v2": 93,
              "label": "Color",
              "position": 1,
              "use_default": false,
              "attribute_code": "color",
              "values": [],
              "product_id": 2048
            },
            {
              "id": 297,
              "attribute_id_v2": 186,
              "label": "Size",
              "position": 0,
              "use_default": false,
              "attribute_code": "size",
              "values": [],
              "product_id": 2048
            }
          ],
          "variants": [
            {
              "product": {
                "id": 2051,
                "name": "Test Configurable Product-M-Black",
                "sku": "test-config-product-M-Black",
                "attribute_set_id": 4,
                "weight": null,
                "price_range": {
                  "minimum_price": {
                    "regular_price": {
                      "value": 100,
                      "currency": "USD"
                    }
                  }
                }
              },
              "attributes": []
            },
            {
              "product": {
                "id": 2052,
                "name": "Test Configurable Product-M-Blue",
                "sku": "test-config-product-M-Blue",
                "attribute_set_id": 4,
                "weight": null,
                "price_range": {
                  "minimum_price": {
                    "regular_price": {
                      "value": 100,
                      "currency": "USD"
                    }
                  }
                }
              },
              "attributes": []
            },
            {
              "product": {
                "id": 2049,
                "name": "Test Configurable Product-S-Black",
                "sku": "test-config-product-S-Black",
                "attribute_set_id": 4,
                "weight": null,
                "price_range": {
                  "minimum_price": {
                    "regular_price": {
                      "value": 100,
                      "currency": "USD"
                    }
                  }
                }
              },
              "attributes": []
            }
          ]
        }
      ]
    }
  }
}
```

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) em nossa documentação de desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis na ferramenta QPT, consulte a seção [Patches disponíveis na ferramenta QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).
