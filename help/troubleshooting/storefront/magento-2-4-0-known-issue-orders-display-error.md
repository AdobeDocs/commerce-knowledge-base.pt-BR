---
title: "Problema conhecido do Adobe Commerce 2.4.0: pedidos exibem erro"
description: '"Este artigo fornece uma solução alternativa para um problema conhecido no Adobe Commerce para um erro de exibição de pedidos. Quando os clientes conectados verificam seus pedidos no menu **Minha conta** (**Minha conta &gt; Meus pedidos**), a grade de pedidos não consegue alternar o número de pedidos por página para 20 a partir da página 2 quando há 11 pedidos. Além disso, se houver mais pedidos do que o configurado para serem mostrados por página, ao navegar até a última página com pedidos, alterar o número de pedidos mostrados por página gerará a mensagem de erro: *Você não fez pedidos*. Este problema será resolvido no Adobe Commerce 2.4.1.'''
exl-id: a6d300e1-1cbc-42b9-997d-d72f8765517b
feature: B2B, Categories, Storefront
role: Admin
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---

# Problema conhecido do Adobe Commerce 2.4.0: erros de exibição de pedidos

Este artigo fornece uma solução alternativa para um problema conhecido no Adobe Commerce para um erro de exibição de pedidos. Quando conectados, os clientes analisam seus pedidos na **Minha conta** menu (**Minha conta > Meus pedidos**), a grade pedidos não consegue alternar o número de pedidos por página para 20 a partir da página 2 quando há 11 pedidos. Além disso, se houver mais pedidos do que o configurado para serem mostrados por página, ao navegar até a última página com pedidos, alterar o número de pedidos mostrados por página gerará a mensagem de erro: *Você não fez nenhum pedido*. Este problema será resolvido no Adobe Commerce 2.4.1.

## Produtos e versões afetados

* Adobe Commerce no local 2.4.0
* Adobe Commerce na infraestrutura em nuvem 2.4.0

## Problema

<u>Pré-requisitos</u>

* O Adobe Commerce 2.4.0 está instalado.
* Crie pelo menos uma categoria e um produto simples.

<u>Etapas a serem reproduzidas</u>

1. Criar 11 pedidos com produtos.
1. Ir para **Minha conta**.
1. Ir para **Meus Pedidos**.
1. Clique na segunda página para exibir a 11ª ordem na grade de pedidos.
1. Selecionar **Mostrar = 20 por página** no menu suspenso.

<u>Resultado esperado</u>

Todos os 11 pedidos são exibidos na primeira página, conforme esperado.

<u>Resultado real</u>

A variável *Você não fez nenhum pedido* é exibida.

## Solução alternativa

A solução alternativa é ter o comprador reaberto **Meus Pedidos** e, em seguida, a lista de pedidos será exibida corretamente. O problema será corrigido na próxima versão, a Adobe Commerce 2.4.1, com lançamento previsto para o quarto trimestre de 2020.

## Leituras relacionadas em nossa base de conhecimento de suporte

* [Problema conhecido do Adobe Commerce 2.4.0: a atualização das Atividades do cliente não funciona](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Problema conhecido do Adobe Commerce 2.4.0: exibição de dados de mensagens brutas na loja](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Problema conhecido do Adobe Commerce 2.4.0: as taxas de imposto de exportação não funcionam](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [O administrador B2B do Adobe Commerce 2.4.0 não pode adicionar o produto configurável à cotação](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
