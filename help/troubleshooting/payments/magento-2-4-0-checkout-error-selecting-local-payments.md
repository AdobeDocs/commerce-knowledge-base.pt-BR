---
title: 'Adobe Commerce 2.4.0: Erro de check-out ao selecionar pagamentos locais'
description: 'Este artigo fala sobre uma solução para um problema conhecido no Adobe Commerce durante a finalização da compra, em que uma mensagem de erro é exibida ao selecionar um método de pagamento local para alguns países. Isso ocorre para os países: Bélgica, Itália, Países Baixos, Polônia e Espanha.'
exl-id: de2eafb0-d03c-4ff8-9615-0f2676d95848
feature: B2B, Categories, Checkout, Orders, Payments
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 8cd50456-5eb0-5364-922a-f14161feb828
    internal-label: Checkout
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 3dcbfa9e-51f8-569c-a0e4-7f59098f730f
    internal-label: Payments
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
  - id: e91a50b1-0b31-436e-9033-00e4776e94cb
    internal-label: Categories
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 0%
---
# Adobe Commerce 2.4.0: Erro de check-out ao selecionar pagamentos locais

Este artigo fala sobre uma solução para um problema conhecido no Adobe Commerce durante a finalização da compra, em que uma mensagem de erro é exibida ao selecionar um método de pagamento local para alguns países. Isso ocorre para os países: Bélgica, Itália, Países Baixos, Polônia e Espanha.

A mensagem de erro, &quot;*Não há métodos de pagamento disponíveis no momento. Atualize seu endereço de cobrança.*&quot; aparecerá, mas os métodos de pagamento locais ainda aparecerão e funcionarão corretamente. Uma correção permanente estará disponível no Adobe Commerce 2.4.1.

## Produtos e versões afetados

* Adobe Commerce no local 2.4.0
* Adobe Commerce na infraestrutura em nuvem 2.4.0

## Problema

<u>Pré-requisitos</u>:

* O Adobe Commerce 2.4.0 está instalado.
* Crie um produto e uma categoria.
* Configure o [Método de Pagamento do Braintree](https://developer.adobe.com/commerce/webapi/graphql/payment-methods/braintree/).

<u>Etapas a serem reproduzidas</u>:

1. Navegue até a loja.
1. Selecione itens para adicionar ao carrinho.
1. Prossiga para o check-out.
1. Preencha o formulário de endereço com um endereço válido.
1. Passe para a página Revisar e Pagamentos.

<u>Resultado esperado</u>:

Os métodos de pagamento locais devem ser exibidos normalmente, sem uma mensagem de erro.

<u>Resultado real</u>:

A mensagem de erro, &quot;*Não há métodos de pagamento disponíveis no momento. Atualize seu endereço de cobrança.*&quot; for exibida, mas os métodos de pagamento locais ainda serão exibidos e funcionarão corretamente.

## Solução

A solução é ignorar a mensagem de erro exibida e continuar com o pagamento normalmente, pois todos os métodos de pagamento locais funcionarão normalmente. A correção estava disponível a partir da versão 2.4.1 do Adobe Commerce.

## Leitura relacionada

* [Problema conhecido do Adobe Commerce 2.4.0: os métodos de pagamento do Braintree não são exibidos na finalização de vários endereços](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
