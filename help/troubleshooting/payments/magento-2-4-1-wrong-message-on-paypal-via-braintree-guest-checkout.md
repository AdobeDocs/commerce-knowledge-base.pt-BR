---
title: "Adobe Commerce 2.4.1: mensagem incorreta na finalização de compra de convidado do PayPal-Braintree"
description: Este artigo descreve um problema conhecido do Adobe Commerce 2.4.1 em que, se o check-out do convidado estiver desativado, um cliente convidado que tenta fazer um pedido no PayPal por meio do Braintree receberá uma mensagem de erro não informativa.
exl-id: 758f5c57-997e-4aca-b299-9934c94fa121
feature: Checkout, Orders, Payments
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 0%

---

# Adobe Commerce 2.4.1: mensagem incorreta na finalização de compra de convidado PayPal-Braintree

Este artigo descreve um problema conhecido do Adobe Commerce 2.4.1 em que, se o check-out do convidado estiver desativado, um cliente convidado que tenta fazer um pedido no PayPal por meio do Braintree receberá uma mensagem de erro não informativa.

## Produtos e versões afetados

* Adobe Commerce no local 2.4.0, 2.4.1
* Adobe Commerce na infraestrutura em nuvem 2.4.0, 2.4.1

## Problema

Um erro inespecífico é exibido quando o check-out do convidado é desativado no back-end e a opção PayPal por meio do Braintree de pagamento é selecionada no Minicarrinho ou no Carrinho de compras.

<u>Pré-requisitos</u>:

1. No Administrador do Commerce, em **Lojas** > **Configuração** > **Vendas** > **Check-out**, defina **Permitir Check-out de Convidado** = *Não*.
1. Ative o PayPal por meio do Braintree, conforme descrito no [Braintree](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/payments/braintree?) em nosso guia do usuário.

<u>Etapas a serem reproduzidas</u>:

1. Adicione o produto ao carrinho como convidado.
1. Selecione **Minicarrinho** e clique em **Pagar com PayPal**.
1. Conclua o checkout do Paypal e você será direcionado para a página de Revisão do pedido.
1. Selecione **Método de envio**.
1. Clique em **Fazer pedido**.

<u>Resultados esperados</u>:

Quando um cliente clica no botão PayPal na página Minicarrinho ou Carrinho de compras, a seguinte mensagem deve ser exibida:

<pre><code class="language-bash">To check out, please sign in with your email address.</code></pre>

Se você habilitar o Paypal direto sem usar o Braintree, este cenário se comporta de forma diferente. Ele não permite que o usuário convidado continue com o processo de pagamento. Ele mostrará a seguinte mensagem quando o usuário convidado clicar no botão PayPal no Minicarrinho:

<pre><code class="language-bash">To check out, please sign in with your email address.</code></pre>

<u>Resultados reais</u>:

O cliente é redirecionado para a página Carrinho de compras e a seguinte mensagem é exibida:

<pre><code class="language-bash">The customer email is missing. Enter and try again.</code></pre>

## Solução alternativa

A solução alternativa para esse problema é que o cliente pode fazer logon em uma loja (usuários conectados não usam o check-out de convidado) onde o check-out de convidado está desativado. Este problema foi corrigido no Adobe Commerce versão 2.4.2.

## Leitura relacionada

* [Prática recomendada para o número de produtos no carrinho na Adobe Commerce](https://support.magento.com/hc/en-us/articles/360048550332) em nossa base de dados de conhecimento de suporte.
* [Tutorial de processamento de pedido: Etapa 1. Adicionar itens ao carrinho](https://developer.adobe.com/commerce/webapi/rest/tutorials/orders/order-add-items/) em nossa documentação do desenvolvedor
* [Tutorial de check-out do GraphQL: Etapa 1. Adicionar produtos ao carrinho](https://developer.adobe.com/commerce/webapi/graphql/tutorials/checkout/checkout-add-product-to-cart.html) em nossa documentação do desenvolvedor
