---
title: "Limpeza de endereço Vertex: endereços diferentes não permitidos"
description: Este artigo fala sobre a solução do problema em que, quando um usuário tenta inserir um **diferente** endereço de faturamento e de envio, com a validação do endereço Vertex ativada, a loja não permitirá que o usuário o insira.
exl-id: a481b044-3b74-4792-abc6-249a182c49e1
feature: B2B, Orders, Shipping/Delivery, Checkout
role: Developer
source-git-commit: 2bba3af8919e1db8482764b8d688f95e606c2683
workflow-type: tm+mt
source-wordcount: '460'
ht-degree: 0%

---

# Limpeza de endereço Vertex: endereços diferentes não permitidos

Este artigo fala sobre a solução do problema em que o usuário tenta inserir um **diferente** endereço de entrega e cobrança, com a validação de endereço Vertex ativada, a loja não permitirá que o usuário a insira.

## Produtos e versões afetados

* Adobe Commerce no local e Adobe Commerce na infraestrutura em nuvem 2.3.5-p1

## Problema

<u>Etapas a serem reproduzidas</u>:

1. Ir para Admin > **Lojas** > **Configuração** > **Vendas** > **Limpeza de endereço**.
1. Selecionar *Ativado* do **Usar limpeza de endereço Vertex** e **Salvar configuração**.
1. Acesse o front-end como convidado e adicione um produto ao carrinho.
1. Clique no ícone Carrinho e **Prosseguir para o check-out**.
1. Preencha os campos de endereço.
1. Selecione o desejado **Método de envio** e clique em **Próxima**.
1. Clique no link **Próxima** botão novamente.
1. Desmarcar **Meu endereço para cobrança e entrega** **são as mesmas** e insira um novo endereço de cobrança (diferente de Endereço).
1. Clique em **Atualizar** e clique em **Atualizar endereço**.

<u>Resultados esperados</u>:

O usuário vê diferentes endereços de faturamento e envio.

<u>Resultados reais</u>:

Quando o usuário pressiona Atualizar, os endereços de faturamento e de envio são revertidos para serem os mesmos.

## Causa

A verificação do endereço de vértice falhou.

## Solução

Desative a verificação de endereço Vertex ou atualize para 2.4.0.

## Leitura relacionada

* [Problema conhecido do Adobe Commerce 2.4.0: mensagem de erro que seleciona o método de pagamento local exibido para alguns países durante a finalização da compra](/help/troubleshooting/payments/magento-2-4-0-checkout-error-selecting-local-payments.md)
* [Problema conhecido do Adobe Commerce 2.4.0: erro 404 ao remover pontos de recompensa na finalização de remessa múltipla](/help/troubleshooting/storefront/magento-2-4-0-404-error-removing-rewards-points-on-multi-shipping-checkout.md)
* [Problema conhecido do Adobe Commerce 2.4.0: erros de exibição de pedidos](/help/troubleshooting/storefront/magento-2-4-0-known-issue-orders-display-error.md)
* [O administrador B2B do Adobe Commerce 2.4.0 não pode adicionar o produto configurável à cotação](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
* [Problema conhecido do Adobe Commerce 2.4.0: os métodos de pagamento de Braintree não são exibidos na finalização de vários endereços](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Problema conhecido na criação de etiquetas de remessa no Adobe Commerce 2.4.0](/help/troubleshooting/known-issues-patches-attached/shipping-labels-creation-known-issue-in-magento-2-4-0.md)
* [Problema conhecido do Adobe Commerce 2.4.0: a atualização das Atividades do cliente não funciona](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Problema conhecido do Adobe Commerce 2.4.0 - as Taxas de imposto de exportação não funcionam](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Problema conhecido do Adobe Commerce 2.4.0: o botão &quot;Adicionar seleções ao carrinho&quot; não funciona](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
* [Problema conhecido do Adobe Commerce 2.4.0: exibição de dados de mensagens brutas na loja](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Problema conhecido do Adobe Commerce 2.4.0: falta o rótulo &quot;Reembolso&quot; no Klarna](/help/troubleshooting/payments/magento-2-4-0-known-issue-missing-refund-label-in-klarna.md)
* [Problema conhecido do Adobe Commerce 2.4.0: dois botões ausentes na página Criar novo pedido no administrador](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-create-new-order-buttons-missing.md)
* [Problema conhecido do Adobe Commerce 2.4.0: quando o Braintree está ativado, o problema de fatura parcial Venmo](/help/troubleshooting/payments/magento-2-4-0-2-4-1-enable-braintree-venmo-partial-invoice-issue.md)
* [Problema conhecido do Adobe Commerce 2.4.0: mensagem de erro que seleciona o método de pagamento local exibido para alguns países durante a finalização da compra](/help/troubleshooting/payments/magento-2-4-0-checkout-error-selecting-local-payments.md)
* [Problema conhecido do Adobe Commerce 2.4.0: Pagamento do Amazon ativado, métodos de pagamento ausentes ao retornar ao checkout padrão usado](/help/troubleshooting/payments/magento-2-4-0-known-issue-amazon-pay-no-payment-methods.md)
* [Problema conhecido do Adobe Commerce 2.4.0: falha na instalação do 2.4.0 com o cache de armazenamentos desatualizado](/help/troubleshooting/installation-and-upgrade/magento-2-4-0-known-issue-2-4-0-installation-fails-with-outdated-stores-cache.md)
