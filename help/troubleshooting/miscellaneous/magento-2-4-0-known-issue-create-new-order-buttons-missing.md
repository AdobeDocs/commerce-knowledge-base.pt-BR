---
title: 'Problema conhecido do Adobe Commerce 2.4.0: os botões Criar novo pedido não aparecem'
description: Este artigo fornece uma solução alternativa para um problema conhecido no Administrador do Commerce para dois botões ausentes na página de criação de pedidos. Ao criar um novo pedido para um cliente novo ou existente, não é possível adicionar produtos ao pedido do catálogo, pois os botões **Adicionar produtos por SKU** e **Adicionar produtos** estão ausentes. Isso é causado pelo empacotamento de JS que está ativado. Uma correção estará disponível no Adobe Commerce 2.4.1.
exl-id: 24ae880e-6d74-4444-9165-2744b12af81a
feature: B2B
role: Developer
source-git-commit: 9cd9720a73b8ecde3baf6a7a5b5732ad1330feee
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 0%

---

# Problema conhecido do Adobe Commerce 2.4.0: os botões Criar novo pedido não aparecem

Este artigo fornece uma solução alternativa para um problema conhecido no Administrador do Commerce para dois botões ausentes na página de criação de pedidos. Ao criar um novo pedido para um cliente novo ou existente, não é possível adicionar produtos ao pedido do catálogo, pois os botões **Adicionar produtos por SKU** e **Adicionar produtos** estão ausentes. Isso é causado pelo empacotamento de JS que está ativado. Uma correção estará disponível no Adobe Commerce 2.4.1.

## Produtos e versões afetados

* Adobe Commerce no local 2.4.0
* Adobe Commerce na infraestrutura em nuvem 2.4.0

## Problema

<u>Etapas a serem reproduzidas</u>

1. Vá para **Clientes > Todos os clientes**.
1. Clique no link **Editar** em um cliente.
1. Clique no botão **Criar Pedido**.

<u>Resultado esperado</u>

Os botões **Adicionar Produtos por SKU** e **Adicionar Produtos** aparecem na página **Criar Novo Pedido**.

<u>Resultado real</u>

Os botões **Adicionar Produtos por SKU** e **Adicionar Produtos** estão ausentes na página **Criar Novo Pedido**.

## Solução alternativa

A solução alternativa para esse problema é desativar o agrupamento JS para a instância do Adobe Commerce. O problema deve ser corrigido no Adobe Commerce 2.4.1, com lançamento previsto para o quarto trimestre de 2020.

## Leituras relacionadas em nossa base de conhecimento de suporte

* [Problema conhecido do Adobe Commerce 2.4.0: as Taxas de imposto de exportação não funcionam](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Problema conhecido do Adobe Commerce 2.4.0: os métodos de pagamento do Braintree não são exibidos na finalização de vários endereços](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Problema conhecido do Adobe Commerce 2.4.0: mensagem de erro que seleciona o método de pagamento local exibido para alguns países durante a finalização da compra](/help/troubleshooting/payments/magento-2-4-0-checkout-error-selecting-local-payments.md)
* [O administrador B2B do Adobe Commerce 2.4.0 não pode adicionar o produto configurável à cotação](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
* [Problema conhecido do Adobe Commerce 2.4.0: a atualização das Atividades do cliente não funciona](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Problema conhecido do Adobe Commerce 2.4.0: o botão &quot;Adicionar seleções ao carrinho&quot; não funciona](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
