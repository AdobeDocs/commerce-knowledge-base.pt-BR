---
title: 'Problema conhecido do Adobe Commerce 2.4.1: erro ao aparecer no Check-out com o Braintree do PayPal'
description: Este artigo descreve um problema conhecido do Adobe Commerce 2.4.1, em que uma mensagem de erro aparece e desaparece na etapa de Faturamento do Check-out se o pagamento do Braintree do PayPal for usado e vários endereços forem selecionados.
exl-id: db3830b2-4885-4d89-85cd-bdcbd4b396e6
feature: Checkout, Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 0%

---

# Problema conhecido do Adobe Commerce 2.4.1: erro ao aparecer no Check-out com o Braintree do PayPal

Este artigo descreve um problema conhecido do Adobe Commerce 2.4.1, em que uma mensagem de erro aparece e desaparece na etapa de Faturamento do Check-out se o pagamento do Braintree do PayPal for usado e vários endereços forem selecionados.

## Produtos e versões afetados

* Adobe Commerce na infraestrutura em nuvem 2.4.1
* Adobe Commerce no local 2.4.1

## Problema

Uma mensagem de erro aparece e desaparece na etapa de Faturamento do Check-out se o pagamento do Braintree do PayPal for usado e vários endereços forem selecionados.

<u>Etapas a serem reproduzidas:</u>

1. Na loja, faça logon como um cliente (opcionalmente, pode ser um check-out de convidado, se estiver ativado em Admin).
1. Adicione um produto ao carrinho.
1. Clique em para abrir a pré-visualização do carrinho.
1. Clique em **Exibir e editar carrinho**.
1. Na página do carrinho, clique em **Fazer Check-out com Vários Endereços**.
1. Clique em **Ir para Informações de Envio** e especifique os endereços.
1. Clique em **Continuar para as Informações de Cobrança**.
1. Selecione **Braintree do PayPal** e clique no botão **PayPal**.
1. Na janela pop-up, clique em **Concordar e pagar**.

<u>Resultado esperado:</u>

O pedido é feito sem nenhum erro.

<u>Resultado real:</u>

O pedido é feito, mas com um erro. Não foi possível inicializar o Check-out do *PayPal. Contate o proprietário da loja*.  é exibido por um segundo e desaparece.

## Correção

Como a colocação do pedido não está bloqueada, não há necessidade de executar etapas alternativas.
