---
title: 'Problema conhecido do Adobe Commerce 2.4.0: pagamento do Amazon, sem métodos de pagamento'
description: Este artigo fornece uma solução para um problema conhecido do Adobe Commerce 2.4.0 em que os métodos de pagamento estão ausentes quando os clientes usam o **Retornar à finalização padrão**, depois de ativarem o pagamento do Amazon.
exl-id: efd792c7-8970-4366-b9d1-4bf284ea96db
feature: B2B, Orders, Payments
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 3dcbfa9e-51f8-569c-a0e4-7f59098f730f
    internal-label: Payments
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '201'
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
* [Problema conhecido do Adobe Commerce 2.4.0: os métodos de pagamento do Braintree não são exibidos na finalização de vários endereços](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
