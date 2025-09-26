---
title: 'Problema conhecido do Adobe Commerce 2.4.0: falta o rótulo "Reembolso" no Klarna'
description: Este artigo fornece uma solução alternativa para um problema conhecido no Admin para um rótulo **Reembolso** ausente no Klarna VBE (Vendor Bundled Extension). Quando estiver no portal Klarna realizando um reembolso, o rótulo **Reembolso** não é exibido ao lado do produto agrupado que foi reembolsado.
exl-id: f08039b2-7f8b-481e-8ec8-1659e227744f
feature: B2B, Orders, Payments
role: Developer
source-git-commit: 9cd9720a73b8ecde3baf6a7a5b5732ad1330feee
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# Problema conhecido do Adobe Commerce 2.4.0: falta o rótulo &quot;Reembolso&quot; no Klarna

Este artigo fornece uma solução alternativa para um problema conhecido no Admin para um rótulo **Reembolso** ausente no Klarna VBE (Vendor Bundled Extension). Quando estiver no portal Klarna realizando um reembolso, o rótulo **Reembolso** não será exibido ao lado do produto Empacotado que foi reembolsado.

## Produtos e versões afetados

* Adobe Commerce no local 2.4.0
* Adobe Commerce na infraestrutura em nuvem 2.4.0

## Problema

<u>Pré-requisitos:</u>

* O Klarna está ativado.
* Um produto agrupado é criado.

<u>Etapas a serem reproduzidas</u>

1. Vá para o front-end do Adobe Commerce e adicione um produto incluído ao **carrinho**.
1. Navegue até check-out.
1. Insira as informações do consumidor no check-out e clique em **Avançar**.
1. Selecione a **opção KP** e clique em **Fazer Pedido**.
1. Vá para **Admin** > **Vendas** > **Pedidos**.
1. Abra o pedido.
1. Criar fatura para o produto.
1. Vá para **Faturas** > **Selecionar fatura** > Clique em **Memorando de Crédito** > Clique em **Reembolso** (Não **Reembolso Offline**).
1. Vá para o portal Klarna.
1. Abra o pedido.
1. O rótulo **Reembolso** está presente.

<u>Resultado esperado</u>

No portal Klarna, o rótulo **Reembolso** é exibido ao lado do produto que foi reembolsado.

<u>Resultado real</u>

No portal Klarna, o rótulo **Reembolso** não é exibido ao lado do produto reembolsado.

## Solução alternativa

A solução alternativa para esse problema é ignorar o rótulo **Reembolso** ausente no portal Klarna para produtos agrupados reembolsados. O reembolso ocorreu, mesmo que o rótulo **Reembolso** não tenha sido exibido. O problema deve ser corrigido no Adobe Commerce 2.4.1, com lançamento previsto para o quarto trimestre de 2020.

## Leituras relacionadas em nossa base de conhecimento de suporte:

* [Problema conhecido do Adobe Commerce 2.4.0: as Taxas de imposto de exportação não funcionam](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Problema conhecido do Adobe Commerce 2.4.0: os métodos de pagamento do Braintree não são exibidos na finalização de vários endereços](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Problema conhecido do Adobe Commerce 2.4.0: mensagem de erro que seleciona o método de pagamento local exibido para alguns países durante a finalização da compra](/help/troubleshooting/payments/magento-2-4-0-checkout-error-selecting-local-payments.md)
* [O administrador B2B do Adobe Commerce 2.4.0 não pode adicionar o produto configurável à cotação](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
* [Problema conhecido do Adobe Commerce 2.4.0: a atualização das Atividades do cliente não funciona](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Problema conhecido do Adobe Commerce 2.4.0: o botão &quot;Adicionar seleções ao carrinho&quot; não funciona](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
