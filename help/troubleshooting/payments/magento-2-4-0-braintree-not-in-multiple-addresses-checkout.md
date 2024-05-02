---
title: "Adobe Commerce 2.4.0: o Braintree não está na finalização de vários endereços"
description: Este artigo fornece uma solução alternativa para um problema conhecido do Adobe Commerce 2.4.0 em que os métodos de pagamento de Braintree não estão incluídos ao trabalhar com a finalização de vários endereços. Observe que o problema foi corrigido no Adobe Commerce 2.4.1.
exl-id: efde0bba-fd4a-490b-becb-856cb9ea58a5
feature: Checkout, Compliance, Orders, Payments, Shipping/Delivery
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 0%

---

# Adobe Commerce 2.4.0: o Braintree não está na finalização de vários endereços

Este artigo fornece uma solução alternativa para um problema conhecido do Adobe Commerce 2.4.0 em que os métodos de pagamento de Braintree não estão incluídos ao trabalhar com a finalização de vários endereços. Observe que o problema foi corrigido no Adobe Commerce 2.4.1.

Observação: a Adobe Commerce recomenda usar o [extensão Commerce Marketplace Braintree](https://marketplace.magento.com/paypal-module-braintree.html) para versões 2.3 e posteriores, a fim de manter a conformidade com o PSD. A extensão não oferece a funcionalidade de finalização de vários endereços.

## Produtos e versões afetados

* Adobe Commerce no local v2.4.0
* Adobe Commerce na infraestrutura em nuvem v2.4.0

## Problema

<u>Pré-requisitos</u>:

A integração de Braintree principal é usada.

<u>Etapas a serem reproduzidas</u>:

1. Vá para a loja.
1. Faça logon como cliente.
1. Adicione um produto ao carrinho.
1. Abra o carrinho.
1. Pressione **Exibir e editar carrinho**.
1. Pressione **Fazer Check-out com Vários Endereços**.
1. Pressione **Ir para Informações de Remessa**.
1. Pressione **Continuar para Informações de Cobrança**.

<u>Resultado esperado</u>:

O Braintree está disponível como um método de pagamento.

<u>Resultado real</u>:

O Braintree não está disponível como um método de pagamento.

## Solução alternativa

Não ative as opções de vários endereços se estiver usando o Braintree no Adobe Commerce 2.4.0. Este problema foi corrigido no Adobe Commerce 2.4.1.

## Leitura relacionada em nossa base de conhecimento de suporte

* [Problema conhecido do Adobe Commerce 2.4.0: a atualização das Atividades do cliente não funciona](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Problema conhecido na criação de etiquetas de remessa no Adobe Commerce 2.4.0](/help/troubleshooting/known-issues-patches-attached/shipping-labels-creation-known-issue-in-magento-2-4-0.md)
* [Problema conhecido do Adobe Commerce 2.4.0: exibição de dados de mensagens brutas na loja](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Problema conhecido do Adobe Commerce 2.4.0 - as Taxas de imposto de exportação não funcionam](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Problema conhecido do Adobe Commerce 2.4.0: o botão &quot;Adicionar seleções ao carrinho&quot; não funciona](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
