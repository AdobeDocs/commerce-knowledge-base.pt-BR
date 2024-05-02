---
title: "Problema do Adobe Commerce 2.4.0: exibição de dados de mensagens brutas da loja"
description: Este artigo fornece uma solução para o problema que ocorre quando todas as mensagens de erro da loja são exibidas com um sinal "+" em vez de um espaço. Essa solução ajuda as mensagens de erro a permanecerem legíveis.
exl-id: f44fe434-a320-4e7e-a876-9575921749f3
feature: Storefront
role: Admin
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 0%

---

# Problema do Adobe Commerce 2.4.0: exibição de dados de mensagem bruta da loja

Este artigo fornece uma solução para o problema que ocorre quando todas as mensagens de erro da loja são exibidas com um sinal &quot;+&quot; em vez de um espaço. Essa solução ajuda as mensagens de erro a permanecerem legíveis.

## Produtos e versões afetados

* Adobe Commerce na infraestrutura em nuvem 2.4.0
* Adobe Commerce no local 2.4.0.

## Problema

<u>Etapas a serem reproduzidas:</u>

1. Ir para **Criar nova conta** página na loja.
1. Crie uma nova conta usando um email registrado. A seguinte mensagem é exibida:

`There+is+already+an+account+with+this+email+address.+If+you+are+sure+that+it+is+your+email+address,+click+here+to+get+your+password+and+access+your+account.`

## Causa

O problema é causado por um problema do PHP 7.4.2 relacionado a set\\read cookies. Consulte [PHP BUG \#79174 setcookie() codifica o espaço como \`+\`, mas $\_COOKIE não os decodifica mais](https://bugs.php.net/bug.php?id=79174).

## Solução

Para resolver este problema use outra versão do PHP 7.4.x. O PHP 7.4.2 não é suportado pelo Adobe Commerce 2.4.0.

## Leituras relacionadas em nossa base de conhecimento de suporte:

* [Problema conhecido do Commerce 2.4.0: os métodos de pagamento de Braintree não são exibidos na finalização de vários endereços](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Problema conhecido na criação de etiquetas de remessa no Adobe Commerce 2.4.0](/help/troubleshooting/known-issues-patches-attached/shipping-labels-creation-known-issue-in-magento-2-4-0.md)
* [Problema conhecido do Adobe Commerce 2.4.0: a atualização das atividades do cliente não funciona](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Problema conhecido do Adobe Commerce 2.4.0: as Taxas de imposto de exportação não funcionam](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Problema conhecido do Adobe Commerce 2.4.0: o botão &quot;Adicionar seleções ao carrinho&quot; não funciona](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
