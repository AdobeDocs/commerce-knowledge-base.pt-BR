---
title: 'Problema conhecido do Adobe Commerce 2.4.1: erro ao sair com o PayPal Braintree'
description: Este artigo descreve um problema conhecido do Adobe Commerce 2.4.1, em que uma mensagem de erro aparece e desaparece na etapa de Faturamento do Check-out se o pagamento do PayPal Braintree for usado e vários endereços forem enviados selecionados.
exl-id: db3830b2-4885-4d89-85cd-bdcbd4b396e6
feature: Checkout, Orders, Payments
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
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '268'
ht-degree: 0%
---
# Problema conhecido do Adobe Commerce 2.4.1: erro ao sair com o PayPal Braintree

Este artigo descreve um problema conhecido do Adobe Commerce 2.4.1, em que uma mensagem de erro aparece e desaparece na etapa de Faturamento do Check-out se o pagamento do PayPal Braintree for usado e vários endereços forem enviados selecionados.

## Produtos e versões afetados

* Adobe Commerce na infraestrutura em nuvem 2.4.1
* Adobe Commerce no local 2.4.1

## Problema

Uma mensagem de erro aparece e desaparece na etapa de Faturamento do Check-out se o pagamento do PayPal Braintree for usado e vários endereços forem selecionados.

<u>Etapas a serem reproduzidas:</u>

1. Na loja, faça logon como um cliente (opcionalmente, pode ser um check-out de convidado, se estiver ativado em Admin).
1. Adicione um produto ao carrinho.
1. Clique em para abrir a pré-visualização do carrinho.
1. Clique em **Exibir e editar carrinho**.
1. Na página do carrinho, clique em **Fazer Check-out com Vários Endereços**.
1. Clique em **Ir para Informações de Envio** e especifique os endereços.
1. Clique em **Continuar para as Informações de Cobrança**.
1. Selecione **PayPal Braintree** e clique no botão **PayPal**.
1. Na janela pop-up, clique em **Concordar e pagar**.

<u>Resultado esperado:</u>

O pedido é feito sem nenhum erro.

<u>Resultado real:</u>

O pedido é feito, mas com um erro. Não foi possível inicializar o Check-out do *PayPal. Contate o proprietário da loja*.  é exibido por um segundo e desaparece.

## Correção

Como a colocação do pedido não está bloqueada, não há necessidade de executar etapas alternativas.
