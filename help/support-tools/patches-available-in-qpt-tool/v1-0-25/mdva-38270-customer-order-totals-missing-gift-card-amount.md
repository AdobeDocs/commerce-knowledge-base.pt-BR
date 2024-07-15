---
title: "MDVA-38270: valor do cartão-presente ausente do Total de pedidos do cliente"
description: O patch MDVA-38270 corrige o problema quando o valor do cartão-presente não é encontrado no Total de pedidos do cliente. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.25 está instalada. A ID do patch é MDVA-38270. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.3.
exl-id: 4ab315c4-d26e-4270-a556-66601d01fb2e
feature: Gift, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# MDVA-38270: valor do cartão-presente ausente do Total de pedidos do cliente

O patch MDVA-38270 corrige o problema quando o valor do cartão-presente não é encontrado no Total de pedidos do cliente. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.25 está instalada. A ID do patch é MDVA-38270. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.3.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**
Adobe Commerce na infraestrutura em nuvem 2.4.2-p1

**Compatível com as versões do Adobe Commerce:**
Adobe Commerce (todos os métodos de implantação) 2.4.1-2.4.2-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O valor do cartão-presente está ausente na resposta total do pedido.

<u>Pré-requisitos</u>:

1. Crie uma conta de cliente.
1. Faça um pedido usando um vale-presente (o vale-presente cobre todo o pedido).

<u>Etapas a serem reproduzidas</u>:

Fazer uma consulta de cliente para cliente, ordens, itens, total:

```GraphQL
query {
  customer {
    orders(
      pageSize: 20
    ) {
      items {
        id
        order_date
        total {
          grand_total {
            value
            currency
          }
          total_giftcard {
              applied_balance {
                value
                currency
              }
              code
              current_balance {
                value
                currency
              }
              expiration_date
          }
        }
        status
      }
    }
  }
}
```

<u>Resultados esperados</u>:

Campo `total_giftcard` disponível.

<u>Resultados reais</u>:

Nenhum campo relacionado a cartão-presente está disponível.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html).

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Para obter informações sobre outros patches disponíveis na ferramenta QPT, consulte a seção [Patches disponíveis na ferramenta QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).
