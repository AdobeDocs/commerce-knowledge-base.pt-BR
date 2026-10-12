---
title: 'Adobe Commerce 2.4.2 B2B: desconto permanece alteração do método de pagamento'
description: Este artigo descreve um problema B2B conhecido do Adobe Commerce 2.4.2 em que um desconto vinculado a um método de pagamento persiste após uma alteração de método de pagamento na finalização da compra. Não há resolução disponível no momento.
exl-id: cd863852-403b-404f-8717-c78c238f5f33
feature: B2B, Orders, Payments, Personalization
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 3dcbfa9e-51f8-569c-a0e4-7f59098f730f
    internal-label: Payments
  - id: f37757d8-3174-5335-b977-1161792f965d
    internal-label: Personalization
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
source-wordcount: '210'
ht-degree: 0%
---
# Adobe Commerce 2.4.2 B2B: desconto permanece alteração do método de pagamento

Este artigo descreve um problema B2B conhecido do Adobe Commerce 2.4.2 em que um desconto vinculado a um método de pagamento persiste após uma alteração de método de pagamento na finalização da compra. Não há resolução disponível no momento.

## Produtos e versões afetados

* Adobe Commerce 2.4.2
* Adobe Commerce na infraestrutura em nuvem 2.4.2
* B2B para Adobe Commerce 1.3.1


## Problema

<u>Etapas a serem reproduzidas</u>:

1. Crie uma **Regra de Preço** do carrinho vinculada a um método de pagamento (Exemplo: os usuários do Paypal recebem um desconto de 20%.).
1. Crie uma Ordem de Compra (OC) e selecione Paypal como método de pagamento. O desconto é aplicado.
1. A OC está aprovada.
1. Ir para a página de pagamento para concluir o pedido.
1. Selecione um método de pagamento diferente.

<u>Resultados reais</u>:

O desconto da forma de pagamento permanece aplicado ao total do pedido.  Nenhuma mensagem de erro é exibida.O proprietário da loja poderá ver que isso ocorreu verificando o histórico do pedido.

<u>Resultados esperados</u> O desconto da forma de pagamento :The foi removido do total do pedido, conforme esperado.

## Solução

Não há resolução disponível no momento.
