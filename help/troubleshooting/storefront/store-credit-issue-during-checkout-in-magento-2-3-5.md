---
title: Problema de crédito de loja durante o check-out no Adobe Commerce 2.3.5
description: Este artigo fornece uma solução alternativa para o problema conhecido relacionado ao crédito da loja durante o check-out no Adobe Commerce 2.3.5, em que os compradores obtêm erros durante o check-out após selecionar e remover o uso do crédito da loja posteriormente. Uma correção permanente estará disponível no Adobe Commerce 2.3.6.
exl-id: a0cca226-4d95-40b3-bd37-f13d28591366
feature: Checkout, Orders, Storefront
role: Admin
source-git-commit: b3d39e6b02728f05f046adf7be94ffacbca944d5
workflow-type: tm+mt
source-wordcount: '284'
ht-degree: 0%

---

# Problema de crédito de loja durante o check-out no Adobe Commerce 2.3.5

Este artigo fornece uma solução alternativa para o problema conhecido relacionado ao crédito da loja durante o check-out no Adobe Commerce 2.3.5, em que os compradores obtêm erros durante o check-out após selecionar e remover o uso do crédito da loja posteriormente. Uma correção permanente estará disponível no Adobe Commerce 2.3.6.

## Produtos e versões afetados

* Adobe Commerce no local 2.3.5
* Adobe Commerce na infraestrutura em nuvem 2.3.5

## Problema

<u>Etapas a serem reproduzidas</u>:

1. O cliente adiciona produtos ao carrinho e prossegue com o checkout.
1. O cliente especifica o crédito de armazenamento como método de pagamento.
1. O cliente remove o crédito da loja e altera o método de pagamento.
1. O cliente prossegue com o check-out.

<u>Resultados esperados</u>:

Todas as informações do pedido são exibidas corretamente.

<u>Resultados reais</u>:

O Adobe Commerce lança um erro na seção Resumo de pedidos da página Pedido.

## Solução

Os clientes podem atualizar a página Pedido e as informações no Resumo de Pedido serão carregadas corretamente. Uma correção estará disponível no Adobe Commerce 2.3.6, com lançamento previsto para o quarto trimestre de 2020.

## Leitura relacionada

Artigos sobre problemas conhecidos do Adobe Commerce 2.3.5 na base de conhecimento de suporte:

* [Pedidos de vários envios com um produto virtual não processado corretamente no Adobe Commerce 2.3.5](/help/troubleshooting/miscellaneous/magento-2-3-5-known-issue-virtual-product-multi-ship-orders.md)

* [Problema conhecido na contagem de produtos da ação em massa no Adobe Commerce 2.3.5](/help/troubleshooting/miscellaneous/bulk-action-product-count-known-issue-in-magento-2-3-5.md)

* [Correção para o problema de checkout de pagamento do Amazon no Adobe Commerce 2.3.5-p1](/help/troubleshooting/payments/patch-for-amazon-pay-checkout-issue-in-magento-2-3-5-p1.md)

* [Problema de comparação de produto no Adobe Commerce 2.3.5](/help/troubleshooting/storefront/product-comparison-known-issue-in-magento-2-3-5.md)

Em nossa documentação do desenvolvedor:

* [Problemas conhecidos do Adobe Commerce 2.3.5](https://commerce-docs.github.io/devdocs-archive/2.3/guides/v2.3/release-notes/release-notes-2-3-5-commerce.html#known-issues)
