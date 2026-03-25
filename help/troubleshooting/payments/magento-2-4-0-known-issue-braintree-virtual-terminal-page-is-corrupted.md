---
title: Página do Terminal virtual do Adobe Commerce 2.4.0 Braintree corrompida
description: Este artigo fornece um patch para o problema conhecido do Adobe Commerce 2.4.0, em que a página Terminal virtual do Braintree não carrega os elementos adequados da interface do usuário ou uma mensagem de erro apropriada se o Braintree não estiver configurado.
exl-id: 1d4d762d-2ab3-4752-ad6d-1eb6a179917d
feature: Orders, Payments
role: Developer
source-git-commit: 1dcd003bd9b08741c0fba464f5520797cfaeccbb
workflow-type: tm+mt
source-wordcount: '288'
ht-degree: 0%

---

# Página do Terminal virtual do Adobe Commerce 2.4.0 Braintree corrompida

Este artigo fornece um patch para o problema conhecido do Adobe Commerce 2.4.0, em que a página Terminal virtual do Braintree não carrega os elementos adequados da interface do usuário ou uma mensagem de erro apropriada se o Braintree não estiver configurado.

## Produtos e versões afetados

* Adobe Commerce no local 2.4.0
* Adobe Commerce na infraestrutura em nuvem 2.4.0

## Problema

### Cenário 1: o método de pagamento do Braintree está configurado

<u>Etapas a serem reproduzidas:</u>

No Commerce Admin, vá para **Vendas** > **Terminal Virtual Braintree** . **&#x200B; **

<u>Resultado esperado:</u>

A página **Terminal Virtual do Braintree** é carregada com a interface do usuário adequada.

<u>Resultado real:</u>

A interface do usuário da página **Terminal Virtual do Braintree** está corrompida.

### Cenário 2: o método de pagamento do Braintree está configurado

<u>Etapas a serem reproduzidas:</u>

No Commerce Admin, vá para **Vendas** > **Terminal Virtual Braintree** . **&#x200B; **

<u>Resultado esperado:</u>

A página **Terminal Virtual do Braintree** é carregada com a interface adequada e um aviso é exibido informando que o Braintree ainda não está configurado.

<u>Resultado real:</u>

A interface do usuário da página **Terminal Virtual do Braintree** está corrompida e nenhum aviso é exibido.

## Solução

Aplique o patch fornecido neste artigo.

## Correção

O patch está anexado a este artigo. Para baixá-lo, role para baixo até o final do artigo e clique no nome do arquivo ou clique no link a seguir:

[BUNDLE-2670-composer.patch](assets/BUNDLE-2670-composer.patch.zip)

### Versões compatíveis do Adobe Commerce:

A correção foi criada para:

* Adobe Commerce na infraestrutura em nuvem 2.4.0
* Adobe Commerce no local 2.4.0

## Como aplicar o patch

Consulte [Como aplicar um patch de compositor fornecido pelo Adobe](https://experienceleague.adobe.com/pt-br/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/how-to-apply-a-composer-patch-provided-by-magento) para obter instruções.

## Arquivos Anexados
