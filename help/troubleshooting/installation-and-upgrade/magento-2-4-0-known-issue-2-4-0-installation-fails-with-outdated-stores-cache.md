---
title: Falha na instalação do Adobe Commerce 2.4.0 com cache de lojas desatualizado
description: 'Este artigo fornece uma solução para o problema em que a instalação do Adobe Commerce 2.4.0 falha com a mensagem de erro: *O site padrão não está definido. Defina o site e tente novamente.* exibido no console.'
exl-id: 0680199b-7e47-4a8c-91fe-9f6c32839a0e
feature: B2B, Cache, Console, Install, Upgrade
role: Developer
source-git-commit: a1046621259ea49eab74cd6ba3bba550e0c70283
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# Falha na instalação do Adobe Commerce 2.4.0 com cache de lojas desatualizado

Este artigo fornece uma solução para o problema em que a instalação do Adobe Commerce 2.4.0 falha com a mensagem de erro: *O site padrão não está definido. Defina o site e tente novamente.* exibido no console.

## Produtos e versões afetados

* Adobe Commerce na infraestrutura em nuvem 2.4.0
* Adobe Commerce no local 2.4.0

## Problema

<u>Pré-requisitos:</u>
Uma extensão de terceiros com dependências em APIs para o módulo Store em comandos CLI está configurada conforme exigido em `composer.json`. Isso faz com que a instalação do Adobe Commerce 2.4.0 falhe com uma mensagem de erro: *O site padrão não está definido. Defina o site e tente novamente.* exibido no console.

## Causa

O problema aparece para as extensões de terceiros que têm dependências de armazenamentos em seus comandos CLI. Um é o Amazon Sales Channel.

## Solução

Antes da instalação do Adobe Commerce 2.4.0, os comerciantes precisam:

1. Remova essas extensões de terceiros de `composer.json`.
1. Instalar o Adobe Commerce sem extensões.
1. Adicione as extensões após a instalação.

O problema será corrigido no escopo da versão 2.4.1 do.

## Leituras relacionadas em nossa base de conhecimento de suporte:

* [Problema conhecido do Adobe Commerce 2.4.0: falta o rótulo &quot;Reembolso&quot; no Klarna](/help/troubleshooting/payments/magento-2-4-0-known-issue-missing-refund-label-in-klarna.md)
* [Problema conhecido do Adobe Commerce 2.4.0: dois botões ausentes na página Criar novo pedido no administrador](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-create-new-order-buttons-missing.md)
* [Adobe Commerce 2.4.0, 2.4.1: Ativar problema de fatura parcial do Braintree Venmo](/help/troubleshooting/payments/magento-2-4-0-2-4-1-enable-braintree-venmo-partial-invoice-issue.md)
* [Problema conhecido do Adobe Commerce 2.4.0: mensagem de erro que seleciona o método de pagamento local exibido para alguns países durante a finalização da compra](/help/troubleshooting/payments/magento-2-4-0-checkout-error-selecting-local-payments.md)
* [Problema conhecido do Adobe Commerce 2.4.0: Pagamento do Amazon ativado, métodos de pagamento ausentes ao retornar ao checkout padrão usado](/help/troubleshooting/payments/magento-2-4-0-known-issue-amazon-pay-no-payment-methods.md)
* [Problema conhecido do Adobe Commerce 2.4.0: erro 404 ao remover pontos de recompensa na finalização de remessa múltipla](/help/troubleshooting/storefront/magento-2-4-0-404-error-removing-rewards-points-on-multi-shipping-checkout.md)
* [Problema conhecido do Adobe Commerce 2.4.0: erros de exibição de pedidos](/help/troubleshooting/storefront/magento-2-4-0-known-issue-orders-display-error.md)
* [O administrador B2B do Adobe Commerce 2.4.0 não pode adicionar o produto configurável à cotação](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
* [Problema conhecido do Adobe Commerce 2.4.0: os métodos de pagamento de Braintree não são exibidos na finalização de vários endereços](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Problema conhecido do Adobe Commerce 2.4.0: a atualização das Atividades do cliente não funciona](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Problema conhecido do Adobe Commerce 2.4.0 - as Taxas de imposto de exportação não funcionam](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Problema conhecido do Adobe Commerce 2.4.0: o botão &quot;Adicionar seleções ao carrinho&quot; não funciona](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
* [Problema conhecido do Adobe Commerce 2.4.0: exibição de dados de mensagens brutas na loja](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
