---
title: "Problema conhecido do Adobe Commerce 2.4.0: pagamento do Amazon, sem métodos de pagamento"
description: Este artigo fornece uma solução para um problema conhecido do Adobe Commerce 2.4.0 em que os métodos de pagamento estão ausentes quando os clientes usam o **Retornar à finalização padrão**, depois de ativarem o pagamento do Amazon.
exl-id: efd792c7-8970-4366-b9d1-4bf284ea96db
feature: B2B, Orders, Payments
role: Developer
source-git-commit: a1046621259ea49eab74cd6ba3bba550e0c70283
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 0%

---

# Problema conhecido do Adobe Commerce 2.4.0: pagamento do Amazon, sem métodos de pagamento

Este artigo fornece uma solução para um problema conhecido do Adobe Commerce 2.4.0 em que os métodos de pagamento estão ausentes quando os clientes usam o **Retornar ao check-out padrão**, depois de habilitarem o pagamento do Amazon.

## Produtos e versões afetados

Adobe Commerce no local e Adobe Commerce na infraestrutura em nuvem v2.3.5.p1 e v2.4.0

<u>Etapas a serem reproduzidas:</u>

1. Navegue até a loja.
1. Adicione qualquer item ao carrinho e prossiga com o check-out.
1. Faça logon em sua conta do Amazon Pay.
1. Selecione um endereço e prossiga para o check-out.
1. Clique em **Retornar ao check-out padrão**.
1. Prossiga para o check-out.

<u>Resultados esperados:</u>

Os métodos de pagamento devem ser exibidos após reiniciar o check-out.

<u>Resultados reais:</u>

Métodos de pagamento ausentes.

## Solução

Uma resolução está planejada para 2.4.1.

## Leituras relacionadas em nossa base de conhecimento de suporte:

* [Problema conhecido do Adobe Commerce 2.4.0: mensagem de erro que seleciona o método de pagamento local exibido para alguns países durante a finalização da compra](/help/troubleshooting/payments/magento-2-4-0-checkout-error-selecting-local-payments.md)
* [Problema conhecido do Adobe Commerce 2.4.0: erro 404 ao remover pontos de recompensa na finalização de remessa múltipla](/help/troubleshooting/storefront/magento-2-4-0-404-error-removing-rewards-points-on-multi-shipping-checkout.md)
* [Problema conhecido do Adobe Commerce 2.4.0: erros de exibição de pedidos](/help/troubleshooting/storefront/magento-2-4-0-known-issue-orders-display-error.md)
* [O administrador B2B do Adobe Commerce 2.4.0 não pode adicionar o produto configurável à cotação](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
* [Problema conhecido do Adobe Commerce 2.4.0: os métodos de pagamento de Braintree não são exibidos na finalização de vários endereços](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Problema conhecido do Adobe Commerce 2.4.0: a atualização das Atividades do cliente não funciona](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Problema conhecido do Adobe Commerce 2.4.0 - as Taxas de imposto de exportação não funcionam](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Problema conhecido do Adobe Commerce 2.4.0: o botão &quot;Adicionar seleções ao carrinho&quot; não funciona](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
* [Problema conhecido do Adobe Commerce 2.4.0: exibição de dados de mensagens brutas na loja](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
