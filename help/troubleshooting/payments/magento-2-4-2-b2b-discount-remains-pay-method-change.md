---
title: 'Adobe Commerce 2.4.2 B2B: desconto permanece alteração do método de pagamento'
description: Este artigo descreve um problema B2B conhecido do Adobe Commerce 2.4.2 em que um desconto vinculado a um método de pagamento persiste após uma alteração de método de pagamento na finalização da compra. Não há resolução disponível no momento.
exl-id: cd863852-403b-404f-8717-c78c238f5f33
feature: B2B, Orders, Payments, Personalization
role: Developer
source-git-commit: 8b6bf1cdada7edb0cdb0bb3e90ed15ee8cebf77e
workflow-type: tm+mt
source-wordcount: '215'
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

O desconto da forma de pagamento permanece aplicado ao total do pedido.  Nenhuma mensagem de erro é exibida. O proprietário da loja poderá ver isso ao verificar o histórico do pedido.

<u>Resultados esperados</u>: o desconto do método de pagamento foi removido do total do pedido, conforme esperado.

## Solução

Não há resolução disponível no momento.
