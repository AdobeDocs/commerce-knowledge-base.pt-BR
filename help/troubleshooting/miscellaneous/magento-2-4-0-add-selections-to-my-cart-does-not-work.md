---
title: 'Adobe Commerce 2.4.0: "Adicionar seleções ao meu carrinho" não funciona'
description: Este artigo fornece uma solução alternativa para um problema conhecido de botão quebrado no Administrador do Commerce ao gerenciar o carrinho de compras de um cliente. Ao tentar adicionar produtos selecionados ao carrinho de compras de um cliente, o botão **Adicionar seleções ao meu carrinho** localizado na parte inferior da seção não funciona. Esse problema ocorre em qualquer página do painel Admin que contém dois botões **Adicionar seleções ao meu carrinho**. Uma correção permanente estará disponível no Adobe Commerce 2.4.1.
exl-id: b0830ec2-2aea-4afb-8d02-e9c8f54283be
feature: Orders, Shopping Cart
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 0%

---

# Adobe Commerce 2.4.0: &quot;Adicionar seleções ao meu carrinho&quot; não funciona

Este artigo fornece uma solução alternativa para um problema conhecido de botão quebrado no Administrador do Commerce ao gerenciar o carrinho de compras de um cliente. Ao tentar adicionar produtos selecionados ao carrinho de compras de um cliente, o botão **Adicionar seleções ao meu carrinho**, localizado na parte inferior da seção, não funciona. Esse problema ocorre em qualquer página do painel Admin que contém dois botões **Adicionar seleções ao meu carrinho**. Uma correção permanente estará disponível no Adobe Commerce 2.4.1.

## Produtos e versões afetados

* Adobe Commerce 2.4.0 (todos os métodos de implantação)

## Problema

<u>Etapas a serem reproduzidas</u>

1. Navegue até qualquer página do painel Admin que contenha dois botões **Adicionar seleções ao meu carrinho**.
1. Selecione itens para adicionar ao meu carrinho.
1. Clique no botão **Adicionar seleções ao meu carrinho**, localizado na parte inferior da seção.

<u>Resultado esperado</u>

Todas as seleções são adicionadas ao meu carrinho conforme esperado.

<u>Resultado real</u>

A Adobe Commerce não adiciona suas seleções ao carrinho.

## Solução

O botão **Adicionar seleções ao meu carrinho**, localizado na parte superior da página, ainda está funcionando. Espera-se que o problema seja corrigido no Adobe Commerce versão 2.4.1, que está programado para ser lançado no quarto trimestre de 2014.

## Leitura relacionada

* [Gerenciamento de um carrinho de compras do MerchDocs](https://experienceleague.adobe.com/pt-br/docs/commerce-admin/stores-sales/point-of-purchase/assist/shopping-assisted-cart-manage) no nosso guia do usuário.
* [Problema conhecido do Adobe Commerce 2.4.0: exibição de dados de mensagens brutas na loja](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md) em nossa base de dados de suporte.
* [Problema conhecido do Adobe Commerce 2.4.0: as Taxas de Imposto sobre Exportação não funcionam](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md) em nossa base de dados de conhecimento de suporte.
* [Problema conhecido do Adobe Commerce 2.4.0: os métodos de pagamento Braintree não aparecem no check-out de Vários Endereços](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md) em nossa base de dados de conhecimento de suporte.
