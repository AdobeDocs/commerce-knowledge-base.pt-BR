---
title: Problema conhecido do Adobe Commerce 2.4.0 - as Taxas de imposto de exportação não funcionam
description: Este artigo fornece uma solução para um problema conhecido do Adobe Commerce 2.4.0 em que o botão **Exportar taxas de imposto** não funciona.
exl-id: 29a34a1f-d23a-43cb-ac1f-8711ce25fa6c
feature: Data Import/Export, Orders
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '237'
ht-degree: 0%

---

# Problema conhecido do Adobe Commerce 2.4.0 - as Taxas de imposto de exportação não funcionam

Este artigo fornece uma solução para um problema conhecido do Adobe Commerce 2.4.0 em que o botão **Exportar Taxas de Imposto** não funciona.

## Produtos e versões afetados

* Adobe Commerce na infraestrutura em nuvem 2.4.0
* Adobe Commerce no local 2.4.0

## Problema

<u>Etapas a serem reproduzidas:</u>

1. Vá para o Painel de Administração do Commerce > **Lojas** > **Regras Fiscais**.
1. Clique no botão **Adicionar Nova Regra de Imposto**.
1. Clique no texto do botão **Exportar Taxas de Imposto**.

   ![magento_export_tax_rates.png](assets/mceclip0.png)

<u>Resultado esperado</u>:

Um arquivo `tax_rates.csv` é baixado contendo alíquotas de imposto.

<u>Resultado real</u>:

Nenhum arquivo .csv foi baixado.

## Solução

Solução alternativa:

Clique na borda inferior esquerda do botão **Exportar Taxas de Imposto** para exportar o arquivo `tax_rates.csv`.

![magento_export_tax_rates.png](assets/mceclip1.png)

Há planos de que o problema seja resolvido em um patch 2.4.1.

## Leitura relacionada

Em nossa base de conhecimento de suporte:

* [Problema conhecido do Adobe Commerce 2.4.0: os métodos de pagamento Braintree não aparecem no check-out de Vários Endereços](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md).
* [Problema conhecido na criação de rótulos de remessa no Adobe Commerce 2.4.0](/help/troubleshooting/known-issues-patches-attached/shipping-labels-creation-known-issue-in-magento-2-4-0.md).
* [Problema conhecido do Adobe Commerce 2.4.0 - a atualização das Atividades do cliente não funciona](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md).
* [Problema conhecido do Adobe Commerce 2.4.0: exibição de dados de mensagens brutas na loja](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md).
* [Problema conhecido do Adobe Commerce 2.4.0: o botão &quot;Adicionar seleções ao carrinho&quot; não funciona](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md).
