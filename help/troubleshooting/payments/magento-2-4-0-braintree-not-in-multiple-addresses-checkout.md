---
title: 'Adobe Commerce 2.4.0: o Braintree não está na finalização de vários endereços'
description: Este artigo fornece uma solução alternativa para um problema conhecido do Adobe Commerce 2.4.0 em que os métodos de pagamento do Braintree não estão incluídos ao trabalhar com a finalização de vários endereços. Observe que o problema foi corrigido no Adobe Commerce 2.4.1.
exl-id: efde0bba-fd4a-490b-becb-856cb9ea58a5
feature: Checkout, Compliance, Orders, Payments, Shipping/Delivery
role: Developer
source-git-commit: 05297c82b292b8ccc88018c58e991bd3a32d6ffa
workflow-type: tm+mt
source-wordcount: '233'
ht-degree: 0%

---

# Adobe Commerce 2.4.0: o Braintree não está na finalização de vários endereços

Este artigo fornece uma solução alternativa para um problema conhecido do Adobe Commerce 2.4.0 em que os métodos de pagamento do Braintree não estão incluídos ao trabalhar com a finalização de vários endereços. Observe que o problema foi corrigido no Adobe Commerce 2.4.1.

Observação: a Adobe Commerce recomenda usar a [extensão do Commerce Marketplace Braintree](https://marketplace.magento.com/paypal-module-braintree.html) para as versões 2.3 e posteriores para manter a conformidade com o PSD. A extensão não oferece a funcionalidade de finalização de vários endereços.

## Produtos e versões afetados

* Adobe Commerce no local v2.4.0
* Adobe Commerce na infraestrutura em nuvem v2.4.0

## Problema

<u>Pré-requisitos</u>:

A integração principal do Braintree é usada.

<u>Etapas a serem reproduzidas</u>:

1. Vá para a loja.
1. Faça logon como cliente.
1. Adicione um produto ao carrinho.
1. Abra o carrinho.
1. Pressione **Exibir e editar carrinho**.
1. Pressione **Verificar com Vários Endereços**.
1. Pressione **Ir para Informações de Envio**.
1. Pressione **Continuar para Informações de Cobrança**.

<u>Resultado esperado</u>:

O Braintree está disponível como um método de pagamento.

<u>Resultado real</u>:

O Braintree não está disponível como um método de pagamento.

## Solução alternativa

Não ative as opções de vários endereços se estiver usando o Braintree no Adobe Commerce 2.4.0. Este problema foi corrigido no Adobe Commerce 2.4.1.
