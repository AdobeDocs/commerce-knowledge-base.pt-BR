---
title: 'Adobe Commerce 2.4.0, 2.4.1: Ativar fatura parcial do Braintree Venmo'
description: Este artigo descreve um problema conhecido do Adobe Commerce 2.4.0 e 2.4.1, em que a fatura parcial não está disponível para pedidos feitos usando o Braintree por meio do Venmo.
exl-id: ef6c8aa4-a2a7-4e07-a957-23173017baf2
feature: Invoices, Orders, Payments
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 591c578b-908e-5b79-a9d3-931dfe60c24c
    internal-label: Invoices
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 3dcbfa9e-51f8-569c-a0e4-7f59098f730f
    internal-label: Payments
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '191'
ht-degree: 0%
---
# Adobe Commerce 2.4.0, 2.4.1: Ativar fatura parcial do Braintree Venmo

Este artigo descreve um problema conhecido do Adobe Commerce 2.4.0 e 2.4.1, em que a fatura parcial não está disponível para pedidos feitos usando o Braintree por meio do Venmo.

## Produtos e versões afetados

* Adobe Commerce no local 2.4.0 e 2.4.1
* Adobe Commerce na infraestrutura em nuvem 2.4.0 e 2.4.1

## Problema

<u>Pré-requisitos:</u>

Na configuração do método de pagamento do Braintree, defina **Habilitar Venmo por meio do Braintree** = *Sim* com **Ação de Pagamento** = *Autorização*; **Habilitar Cofre para Pagamentos com Cartão** = *Não*.

<u>Etapas a serem reproduzidas:</u>

1. Crie um pedido para dois ou mais produtos usando o Venmo (Braintree) como método de pagamento.
1. Abra o pedido no Administrador do Commerce.
1. Crie uma fatura para um dos produtos solicitados.
1. Tente criar uma fatura para os produtos restantes encomendados.

<u>Resultado esperado:</u>

Fatura criada.

<u>Resultado real:</u>

A seguinte mensagem de erro é exibida: *O comando &quot;vault\_capture&quot; não existe. Verifique o comando e tente novamente.*

## Solução alternativa

Registre o valor total ao criar faturas para pedidos feitos usando o Braintree por meio do Venmo.
