---
title: "Adobe Commerce 2.4.0: exceção durante a instalação B2B 1.2.0"
description: Este artigo fornece uma correção para um problema conhecido do Adobe Commerce para uma exceção lançada durante "setup:upgrade" ao instalar o B2B 1.2.0.
exl-id: 2c1dadd9-7754-4b4c-8d37-b75c13beae5c
feature: B2B, Install, Upgrade
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '393'
ht-degree: 0%

---

# Adobe Commerce 2.4.0: exceção durante a instalação do B2B 1.2.0

Este artigo fornece uma correção para um problema conhecido do Adobe Commerce para uma exceção lançada durante `setup:upgrade` ao instalar o B2B 1.2.0.

## Produtos e versões afetados

* Adobe Commerce no local 2.4.0
* Adobe Commerce na infraestrutura em nuvem 2.4.0
* B2B 1.2.0

## Problema

<u>Etapas a serem reproduzidas</u>

1. Instale o Adobe Commerce com mais de um armazenamento criado.
1. Criar um armazenamento adicional.
1. Instale o B2B 1.2.0.

>[!WARNING]
>
>A atualização de qualquer instância B2B com mais de um armazenamento de uma versão inferior a 1.2.0 ou instância do Commerce inferior a 2.4.0 também é afetada.

<u>Resultado esperado</u>

Instalações do B2B 1.2.0.

<u>Resultado real</u>

Quando o `setup:upgrade` é executado para instalar o B2B 1.2.0, este erro aparece no módulo `PurchaseOrder`:

```php
Module 'Magento_PurchaseOrder':
  Unable to apply data patch Magento\PurchaseOrder\Setup\Patch\Data\InitPurchaseOrderSalesSequence
  for module Magento_PurchaseOrder. Original exception message: DDL statements
  are not allowed in transactions
```

## Solução

Aplique o patch fornecido neste artigo.

## Correção

O patch está anexado a este artigo, disponível para download nos formatos `.composer` e `.git` (após descompactar os arquivos).

Para baixá-lo, role para baixo até o final do artigo e clique no nome do arquivo ou clique em um dos links a seguir:

* [Composer patch B2B-716\_composer.patch](assets/B2B-716_composer.patch.zip)
* [Git patch B2B-716\_git.patch](assets/B2B-716_git.patch.zip)

## Como aplicar um patch

<u>Correção do compositor </u>

Consulte [Como aplicar um patch de compositor fornecido pelo Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) para obter instruções de patch de compositor.

<u>Patch do Git </u>

* Consulte [Aplicar patches](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) na documentação do desenvolvedor para obter instruções de patch do Git para o Adobe Commerce na infraestrutura em nuvem.
* Consulte [Aplicação de patches: patches personalizados](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/patches/overview#custom-patches) na documentação do desenvolvedor para obter instruções sobre patch do Git para o Adobe Commerce.

## Leitura relacionada

* [Problema conhecido do Adobe Commerce 2.4.0: exibição de dados de mensagens brutas na loja](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Problema conhecido do Adobe Commerce 2.4.0: as Taxas de imposto de exportação não funcionam](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Problema conhecido do Adobe Commerce 2.4.0: os métodos de pagamento de Braintree não são exibidos na finalização de vários endereços](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Problema conhecido do Adobe Commerce 2.4.0: mensagem de erro que seleciona o método de pagamento local exibido para alguns países durante a finalização da compra](/help/troubleshooting/payments/magento-2-4-0-checkout-error-selecting-local-payments.md)
* [Problema conhecido do Adobe Commerce 2.4.0: erro 404 ao remover pontos de recompensa na finalização de remessa múltipla](/help/troubleshooting/storefront/magento-2-4-0-404-error-removing-rewards-points-on-multi-shipping-checkout.md)
* [Problema conhecido do Adobe Commerce 2.4.0: erros de exibição de pedidos](/help/troubleshooting/storefront/magento-2-4-0-known-issue-orders-display-error.md)
* [O administrador B2B do Adobe Commerce 2.4.0 não pode adicionar o produto configurável à cotação](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
* [Problema conhecido do Adobe Commerce 2.4.0: a atualização das Atividades do cliente não funciona](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Problema conhecido do Adobe Commerce 2.4.0: o botão &quot;Adicionar seleções ao carrinho&quot; não funciona](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
