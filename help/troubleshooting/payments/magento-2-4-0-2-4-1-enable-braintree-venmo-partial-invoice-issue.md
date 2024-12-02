---
title: 'Adobe Commerce 2.4.0, 2.4.1: Ativar fatura parcial do Braintree Venmo'
description: Este artigo descreve um problema conhecido do Adobe Commerce 2.4.0 e 2.4.1, em que a fatura parcial não está disponível para pedidos feitos usando o Braintree pelo Venmo.
exl-id: ef6c8aa4-a2a7-4e07-a957-23173017baf2
feature: Invoices, Orders, Payments
role: Developer
source-git-commit: 8b6bf1cdada7edb0cdb0bb3e90ed15ee8cebf77e
workflow-type: tm+mt
source-wordcount: '202'
ht-degree: 0%

---

# Adobe Commerce 2.4.0, 2.4.1: Ativar fatura parcial do Braintree Venmo

Este artigo descreve um problema conhecido do Adobe Commerce 2.4.0 e 2.4.1, em que a fatura parcial não está disponível para pedidos feitos usando o Braintree pelo Venmo.

## Produtos e versões afetados

* Adobe Commerce no local 2.4.0 e 2.4.1
* Adobe Commerce na infraestrutura em nuvem 2.4.0 e 2.4.1

## Problema

<u>Pré-requisitos:</u>

Na configuração do método de pagamento Braintree, defina **Habilitar Venmo por meio de Braintree** = *Sim* com **Ação de Pagamento** = *Autorização*; **Habilitar Cofre para Pagamentos com Cartão** = *Não*.

<u>Etapas a serem reproduzidas:</u>

1. Crie um pedido para dois ou mais produtos usando Venmo (Braintree) como método de pagamento.
1. Abra o pedido no Administrador do Commerce.
1. Crie uma fatura para um dos produtos solicitados.
1. Tente criar uma fatura para os produtos restantes encomendados.

<u>Resultado esperado:</u>

Fatura criada.

<u>Resultado real:</u>

A seguinte mensagem de erro é exibida: *O comando &quot;vault\_capture&quot; não existe. Verifique o comando e tente novamente.*

## Solução alternativa

Registre o valor total ao criar faturas para pedidos feitos usando o Braintree por meio do Venmo.
