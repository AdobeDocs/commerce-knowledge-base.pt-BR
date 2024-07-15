---
title: "Correção do Adobe Commerce 2.4.0: retorna o problema de criação de etiqueta de envio"
description: Este artigo fornece um patch para o problema conhecido do Adobe Commerce 2.4.0 quando há um problema com a impressão de uma etiqueta de envio para as devoluções dos clientes.
exl-id: f78f8d7e-29e9-4d6c-83f6-cd5afa1d7d9c
feature: B2B, Orders, Returns, Communications, Shipping/Delivery
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---

# Correção do Adobe Commerce 2.4.0: retorna o problema de criação de etiqueta de envio

Este artigo fornece um patch para o problema conhecido do Adobe Commerce 2.4.0 quando há um problema com a impressão de uma etiqueta de envio para as devoluções dos clientes.

## Produtos e versões afetados

* Adobe Commerce na infraestrutura em nuvem 2.4.0
* Adobe Commerce no local 2.4.0

## Problema

<u>Etapas a serem reproduzidas:</u>

1. Faça e conclua um pedido com um dos seguintes métodos principais de envio: FedEx, DHL, UPS e USPS.
1. Crie e autorize devoluções para este pedido.
1. Abra uma página **Informações de Retorno** autorizada e clique no botão **Criar Etiqueta de Envio**.
1. Selecione o método de envio, adicione um produto a um pacote e clique em Salvar.

<u>Resultado esperado:</u>

Um rótulo de remessa foi criado com êxito e você verá uma mensagem: *Você criou um rótulo de remessa.*

<u>Resultado real:</u>

A página **Informações de Retorno** está corrompida e você verá uma mensagem de erro na página Informações de Retorno: *Foram feitas alterações nesta seção que não foram salvas. Esta guia contém dados inválidos*.

## Solução

Aplique o [patch](assets/MC-35984-2.4.0-CE-composer.patch.zip) fornecido neste artigo.

## Correção

O patch está anexado a este artigo. Para baixá-lo, role para baixo até o final do artigo e clique no nome do arquivo ou clique no link a seguir:

[MC-35984-2.4.0-CE-composer.patch](assets/MC-35984-2.4.0-CE-composer.patch.zip)

O patch também está disponível para download nos formatos `.git` e `.composer`, na página [Downloads da Adobe Commerce](https://magento.com/tech-resources/download), em **Patches**, na navegação de coluna à esquerda. Procure o patch MC-35984.

## Como aplicar o patch

Para obter instruções, consulte [Como aplicar um patch de compositor fornecido pelo Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) em nossa página de conhecimento de suporte.

## Leituras relacionadas em nossa base de conhecimento de suporte:

* [Problema conhecido do Adobe Commerce 2.4.0: exibição de dados de mensagens brutas na loja](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Problema conhecido do Adobe Commerce 2.4.0: as Taxas de imposto de exportação não funcionam](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Problema conhecido do Adobe Commerce 2.4.0: o botão &quot;Adicionar seleções ao carrinho&quot; não funciona](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
* [Problema conhecido do Adobe Commerce 2.4.0: os métodos de pagamento de Braintree não são exibidos na finalização de vários endereços](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [O administrador B2B do Adobe Commerce 2.4.0 não pode adicionar o produto configurável à cotação](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
* [Problema conhecido do Adobe Commerce 2.4.0: erros de exibição de pedidos](/help/troubleshooting/storefront/magento-2-4-0-known-issue-orders-display-error.md)
* [Problema conhecido na criação de etiquetas de remessa no Adobe Commerce 2.4.0](/help/troubleshooting/known-issues-patches-attached/shipping-labels-creation-known-issue-in-magento-2-4-0.md)
