---
title: 'Problema conhecido do Adobe Commerce 2.4.0: falta o rótulo "Reembolso" no Klarna'
description: Este artigo fornece uma solução alternativa para um problema conhecido no Admin para um rótulo **Reembolso** ausente no Klarna VBE (Vendor Bundled Extension). Quando estiver no portal Klarna realizando um reembolso, o rótulo **Reembolso** não é exibido ao lado do produto agrupado que foi reembolsado.
exl-id: f08039b2-7f8b-481e-8ec8-1659e227744f
feature: B2B, Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '436'
ht-degree: 0%

---

# Problema conhecido do Adobe Commerce 2.4.0: falta o rótulo &quot;Reembolso&quot; no Klarna

Este artigo fornece uma solução alternativa para um problema conhecido no Admin para um **Reembolso** rótulo no Klarna VBE (Vendor Bundled Extension). Quando, no portal Klarna, é efetuado um reembolso, a **Reembolso** rótulo não é exibido ao lado do produto Empacotado que foi reembolsado.

## Produtos e versões afetados

* Adobe Commerce no local 2.4.0
* Adobe Commerce na infraestrutura em nuvem 2.4.0

## Problema

<u>Pré-requisitos:</u>

* O Klarna está ativado.
* Um produto agrupado é criado.

<u>Etapas a serem reproduzidas</u>

1. Acesse o front-end do Adobe Commerce e adicione um produto incluído ao **carrinho**.
1. Navegue até check-out.
1. Insira as informações do consumidor no check-out e clique em **Próxima**.
1. Selecionar **Opção KP** e clique em **Fazer pedido**.
1. Ir para **Admin** > **Vendas** > **Pedidos**.
1. Abra o pedido.
1. Criar fatura para o produto.
1. Ir para **Faturas** > **Selecionar fatura** > Clique **Aviso de Crédito** > Clique **Reembolso** (Não **Reembolso offline**).
1. Vá para o portal Klarna.
1. Abra o pedido.
1. A variável **Reembolso** rótulo está presente.

<u>Resultado esperado</u>

No portal Klarna, o **Reembolso** rótulo é exibido ao lado do produto que foi reembolsado.

<u>Resultado real</u>

No portal Klarna, o **Reembolso** rótulo não é exibido ao lado do produto reembolsado.

## Solução alternativa

A solução alternativa para esse problema é ignorar o **Reembolso** no portal Klarna para os produtos agrupados reembolsados. O reembolso ocorreu, mesmo que o **Reembolso** o rótulo não foi exibido. O problema deve ser corrigido no Adobe Commerce 2.4.1, com lançamento previsto para o quarto trimestre de 2020.

## Leituras relacionadas em nossa base de conhecimento de suporte:

* [Problema conhecido do Adobe Commerce 2.4.0: exibição de dados de mensagens brutas na loja](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Problema conhecido do Adobe Commerce 2.4.0: as Taxas de imposto de exportação não funcionam](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Problema conhecido do Adobe Commerce 2.4.0: os métodos de pagamento de Braintree não são exibidos na finalização de vários endereços](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Problema conhecido do Adobe Commerce 2.4.0: mensagem de erro que seleciona o método de pagamento local exibido para alguns países durante a finalização da compra](/help/troubleshooting/payments/magento-2-4-0-checkout-error-selecting-local-payments.md)
* [Problema conhecido do Adobe Commerce 2.4.0: erro 404 ao remover pontos de recompensa na finalização de remessa múltipla](/help/troubleshooting/storefront/magento-2-4-0-404-error-removing-rewards-points-on-multi-shipping-checkout.md)
* [Problema conhecido do Adobe Commerce 2.4.0: erros de exibição de pedidos](/help/troubleshooting/storefront/magento-2-4-0-known-issue-orders-display-error.md)
* [O administrador B2B do Adobe Commerce 2.4.0 não pode adicionar o produto configurável à cotação](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
* [Problema conhecido na criação de etiquetas de remessa no Adobe Commerce 2.4.0](/help/troubleshooting/known-issues-patches-attached/shipping-labels-creation-known-issue-in-magento-2-4-0.md)
* [Problema conhecido do Adobe Commerce 2.4.0: a atualização das Atividades do cliente não funciona](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Problema conhecido do Adobe Commerce 2.4.0: o botão &quot;Adicionar seleções ao carrinho&quot; não funciona](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
