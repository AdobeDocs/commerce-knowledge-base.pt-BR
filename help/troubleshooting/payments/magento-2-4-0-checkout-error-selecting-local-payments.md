---
title: "Adobe Commerce 2.4.0: erro de check-out ao selecionar pagamentos locais"
description: "Este artigo fala sobre uma solução para um problema conhecido no Adobe Commerce durante a finalização da compra, em que uma mensagem de erro é exibida ao selecionar um método de pagamento local para alguns países. Isso ocorre para os países: Bélgica, Itália, Holanda, Polônia e Espanha."
exl-id: de2eafb0-d03c-4ff8-9615-0f2676d95848
feature: B2B, Categories, Checkout, Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---

# Adobe Commerce 2.4.0: Erro de check-out ao selecionar pagamentos locais

Este artigo fala sobre uma solução para um problema conhecido no Adobe Commerce durante a finalização da compra, em que uma mensagem de erro é exibida ao selecionar um método de pagamento local para alguns países. Isso ocorre para os países: Bélgica, Itália, Países Baixos, Polônia e Espanha.

A mensagem de erro, &quot;*Não há métodos de pagamento disponíveis no momento. Atualize seu endereço de cobrança.*&quot; aparecerá, mas os métodos de pagamento locais ainda aparecerão e funcionarão corretamente. Uma correção permanente estará disponível no Adobe Commerce 2.4.1.

## Produtos e versões afetados

* Adobe Commerce no local 2.4.0
* Adobe Commerce na infraestrutura em nuvem 2.4.0

## Problema

<u>Pré-requisitos</u>:

* O Adobe Commerce 2.4.0 está instalado.
* Crie um produto e uma categoria.
* Configurar [Método De Pagamento Braintree](https://devdocs.magento.com/guides/v2.4/graphql/payment-methods/braintree.html).

<u>Etapas a serem reproduzidas</u>:

1. Navegue até a loja.
1. Selecione itens para adicionar ao carrinho.
1. Prossiga para o check-out.
1. Preencha o formulário de endereço com um endereço válido.
1. Passe para a página Revisar e Pagamentos.

<u>Resultado esperado</u>:

Os métodos de pagamento locais devem ser exibidos normalmente, sem uma mensagem de erro.

<u>Resultado real</u>:

A mensagem de erro, &quot;*Não há métodos de pagamento disponíveis no momento. Atualize seu endereço de cobrança.*&quot; aparece, mas os métodos de pagamento locais ainda serão exibidos e funcionarão corretamente.

## Solução

A solução é ignorar a mensagem de erro exibida e continuar com o pagamento normalmente, pois todos os métodos de pagamento locais funcionarão normalmente. A correção estava disponível a partir da versão 2.4.1 do Adobe Commerce.

## Leitura relacionada

* [Problema conhecido do Adobe Commerce 2.4.0: exibição de dados de mensagens brutas na loja](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Problema conhecido do Adobe Commerce 2.4.0: as Taxas de imposto de exportação não funcionam](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Problema conhecido do Adobe Commerce 2.4.0: os métodos de pagamento de Braintree não são exibidos na finalização de vários endereços](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Problema conhecido do Adobe Commerce 2.4.0: retorna a página de edição para de funcionar ao criar o rótulo de remessa](/help/troubleshooting/known-issues-patches-attached/magento-2-4-0-patch-returns-shipping-label-creation-issue.md)
* [Problema conhecido do Adobe Commerce 2.4.0: a atualização das Atividades do cliente não funciona](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [O administrador B2B do Adobe Commerce 2.4.0 não pode adicionar o produto configurável à cotação](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
