---
title: 'Adobe Commerce 2.4.2: o pagamento do Braintree Venmo não funciona'
description: Este artigo descreve um problema conhecido do Adobe Commerce 2.4.2 em que os pedidos não são gerados ao usar o Braintree Venmo durante a finalização da compra. Não há resolução disponível no momento.
exl-id: 1832ab64-5024-444b-915e-473b34979a6e
feature: Orders, Payments
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 3dcbfa9e-51f8-569c-a0e4-7f59098f730f
    internal-label: Payments
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '200'
ht-degree: 0%
---
# Adobe Commerce 2.4.2: o pagamento do Braintree Venmo não funciona

Este artigo descreve um problema conhecido do Adobe Commerce 2.4.2 em que os pedidos não são gerados ao usar o Braintree Venmo durante a finalização da compra. Não há resolução disponível no momento.

## Produtos e versões afetados

* Adobe Commerce (todos os métodos de implantação) 2.4.2

## Problema

<u>Pré-condição</u> :

Ativar pagamento Venmo na configuração do Braintree.

<u>Etapas a serem reproduzidas</u>:

1. Na loja, adicione qualquer item ao carrinho de compras.
1. Vá para **Check-out**.
1. Selecione o método de envio apropriado.
1. Selecione **Venmo** como método de pagamento.
1. Clique em **Pagar com Venmo**.
1. Clique em **Fazer pedido**.

<u>Resultados reais</u>:

O pedido não é criado no código Adobe Commerce depois que o cliente é redirecionado de volta para a loja a partir do aplicativo Venmo, e nenhuma mensagem de erro é exibida. O pedido é criado no Braintree.

<u>Resultados esperados</u>:

O pedido é criado no Adobe Commerce depois que o cliente é redirecionado de volta para a loja a partir do aplicativo Venmo e o pedido é criado no Braintree, conforme esperado.

## Solução

Não há resolução disponível no momento.
