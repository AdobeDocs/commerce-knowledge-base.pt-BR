---
title: "MDVA-37288: Preços de camada incorretos retornados após a solicitação do GraphQL"
description: O patch de qualidade MDVA-37288 para Adobe Commerce resolve o problema em que os preços de nível errados são retornados após a solicitação do GraphQL. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) v.1.0.23 está instalada. Observe que o problema está programado para ser corrigido no Adobe Commerce versão 2.4.3.
exl-id: d2cf24d5-6163-4968-a89c-b7407d439e1c
feature: GraphQL, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '412'
ht-degree: 0%

---

# MDVA-37288: Preços de camada incorretos retornados após a solicitação do GraphQL

O patch de qualidade MDVA-37288 para Adobe Commerce resolve o problema em que os preços de nível errados são retornados após a solicitação do GraphQL. Este patch está disponível quando a variável [Ferramenta de correções de qualidade (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) O v.1.0.23 está instalado. Observe que o problema está programado para ser corrigido no Adobe Commerce versão 2.4.3.

## Produtos e versões afetados

* O patch foi projetado para Adobe Commerce na infraestrutura em nuvem 2.4.2
* O patch também é compatível com o Adobe Commerce no local e o Adobe Commerce na infraestrutura em nuvem 2.4.2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

<u>Etapas a serem reproduzidas</u>:

1. Adicionar preços de camada a qualquer item (para este exemplo, os preços de camada foram adicionados a itens com id=1 e id=2).
1. Execute a consulta do GraphQL com a pesquisa que incluirá os itens com preços de camada e itens sem preços de camada.

<pre><code class="language-graphql">
{
  products(pageSize: 20, currentPage: 1, search: "24-MB0") {
    items {
      id
      price_tiers {
        quantity
        final_price {
          value
        }
      }
    }
  }
}
</code></pre>

<u>Resultados esperados</u>:

Somente itens com preços de nível devem retornar preços de nível adequados:

```json
{
  "data": {
        "products": {
            "items": [
                {
                    "id": 17,
                    "price_tiers": []
                },
                {
                    "id": 1,
                    "price_tiers": [
                        {
                            "quantity": 1,
                            "final_price": {
                                "value": 34
                            }
                        },
                        {
                            "quantity": 5,
                            "final_price": {
                                "value": 32
                            }
                        }
                    ]
                },
                {
                    "id": 23,
                    "price_tiers": []
                },
                {
                    "id": 19,
                    "price_tiers": []
                }
            ]
        }
    }
}
```

<u>Resultados reais</u>:

* Todos os itens que vêm depois de um item com preços de camada têm preços de camada na resposta.
* Os dados de preços de camada retornados são do último item no loop que tinha preços de camada.

exemplo de resposta:

```json
{
    "data": {
        "products": {
            "items": [
                {
                    "id": 17,
                    "price_tiers": []
                },
                {
                    "id": 1,
                    "price_tiers": [
                        {
                            "quantity": 1,
                            "final_price": {
                                "value": 34
                            }
                        },
                        {
                            "quantity": 5,
                            "final_price": {
                                "value": 32
                            }
                        }
                    ]
                },
                {
                    "id": 23,
                    "price_tiers": [
                        {
                            "quantity": 1,
                            "final_price": {
                                "value": 34
                            }
                        },
                        {
                            "quantity": 5,
                            "final_price": {
                                "value": 32
                            }
                        }
                    ]
                },
                {
                    "id": 19,
                    "price_tiers": [
                        {
                            "quantity": 1,
                            "final_price": {
                                "value": 34
                            }
                        },
                        {
                            "quantity": 5,
                            "final_price": {
                                "value": 32
                            }
                        }
                    ]
                }
            ]
        }
    }
}
```


## Aplicar o patch

Para aplicar patches individuais, use os seguintes links na documentação do desenvolvedor, dependendo do seu produto Adobe Commerce:

* Adobe Commerce e Magento Open Source no local: [Guia de atualização de software > Aplicar patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://devdocs.magento.com/cloud/project/project-patch.html)

## Leitura relacionada

Para saber mais sobre a Ferramenta de correções de qualidade em nossa base de conhecimento de suporte, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatendimento de correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de patches de qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)

Para obter informações sobre outros patches disponíveis na ferramenta QPT, consulte o [Correções disponíveis na ferramenta QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) seção em nossa base de conhecimento de suporte.
