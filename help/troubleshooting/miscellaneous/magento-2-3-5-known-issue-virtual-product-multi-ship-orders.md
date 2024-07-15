---
title: "Problema conhecido do Adobe Commerce 2.3.5: pedidos virtuais de várias entregas"
description: Este artigo explica um problema conhecido no Adobe Commerce 2.3.5 em que um pedido de vários envios contendo um produto virtual não é processado corretamente.
exl-id: 34ce79a2-5157-492b-8ee4-bdc09aae0c40
feature: Orders, Products, Shipping/Delivery
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '224'
ht-degree: 0%

---

# Problema conhecido do Adobe Commerce 2.3.5: pedidos virtuais de vários envios

Este artigo explica um problema conhecido no Adobe Commerce 2.3.5 em que um pedido de vários envios contendo um produto virtual não é processado corretamente.

## Produtos e versões afetados

* Adobe Commerce no local 2.3.5
* Adobe Commerce na infraestrutura em nuvem 2.3.5

## Problema

<u>Etapas a serem reproduzidas</u>:

1. Na loja, adicione produtos físicos e virtuais ao carrinho.
1. Vá para o check-out e selecione **Check-out com Vários Endereços**.
1. Adicione todas as informações necessárias e faça o pedido.

<u>Resultado esperado</u>:

Os pedidos são feitos para todos os produtos com êxito.

<u>Resultado real</u>:

O pedido do produto virtual está vazio.

## Correção

Uma correção estará disponível no Adobe Commerce 2.3.6, com lançamento previsto para o quarto trimestre de 2020.

## Leitura relacionada

Em nossa base de conhecimento de suporte:

* [Problema conhecido de comparação de produto no Adobe Commerce 2.3.5](/help/troubleshooting/storefront/product-comparison-known-issue-in-magento-2-3-5.md)
* [Problema conhecido na contagem de produtos da ação em massa no Adobe Commerce 2.3.5](/help/troubleshooting/miscellaneous/bulk-action-product-count-known-issue-in-magento-2-3-5.md)
* [Emissão do método de pagamento do país no Adobe Commerce 2.3.5 e 2.3.5-p1](/help/troubleshooting/known-issues-patches-attached/magento-2-3-5-2-3-5-p1-patch-country-payment-issue.md)
* [O Adobe Commerce solicita que os clientes façam logon, mas fornece link inválido](/help/troubleshooting/known-issues-patches-attached/magento-prompts-customers-log-in-invalid-link.md)
* [Correção para o problema de checkout de pagamento do Amazon no Adobe Commerce 2.3.5-p1](/help/troubleshooting/payments/patch-for-amazon-pay-checkout-issue-in-magento-2-3-5-p1.md)

Em nossa documentação do desenvolvedor:

* [Notas de versão do Adobe Commerce 2.3.5](https://devdocs.magento.com/guides/v2.3/release-notes/release-notes-2-3-5-commerce.html#known-issues)
