---
title: Página do terminal virtual do Braintree Adobe Commerce 2.4.0 corrompida
description: Este artigo fornece um patch para o problema conhecido do Adobe Commerce 2.4.0, em que a página Braintree Virtual Terminal não carrega os elementos adequados da interface do usuário ou uma mensagem de erro apropriada se o Braintree não estiver configurado.
exl-id: 1d4d762d-2ab3-4752-ad6d-1eb6a179917d
feature: Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 0%

---

# Página do terminal virtual do Braintree Adobe Commerce 2.4.0 corrompida

Este artigo fornece um patch para o problema conhecido do Adobe Commerce 2.4.0, em que a página Braintree Virtual Terminal não carrega os elementos adequados da interface do usuário ou uma mensagem de erro apropriada se o Braintree não estiver configurado.

## Produtos e versões afetados

* Adobe Commerce no local 2.4.0
* Adobe Commerce na infraestrutura em nuvem 2.4.0

## Problema

### Cenário 1: o método de pagamento Braintree está configurado

<u>Etapas a serem reproduzidas:</u>

No Commerce Admin, vá para **Vendas** > **Terminal Virtual Braintree** . **&#x200B; **

<u>Resultado esperado:</u>

A página **Terminal Virtual do Braintree** é carregada com a interface do usuário adequada.

<u>Resultado real:</u>

A interface do usuário da página **Terminal Virtual Braintree** está corrompida.

### Cenário 2: o método de pagamento Braintree está configurado

<u>Etapas a serem reproduzidas:</u>

No Commerce Admin, vá para **Vendas** > **Terminal Virtual Braintree** . **&#x200B; **

<u>Resultado esperado:</u>

A página **Terminal Virtual de Braintree** é carregada com a interface adequada e um aviso é exibido informando que o Braintree ainda não está configurado.

<u>Resultado real:</u>

A interface do usuário da página **Terminal Virtual Braintree** está corrompida e nenhum aviso é exibido.

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

Consulte [Como aplicar um patch de compositor fornecido pelo Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) para obter instruções.

## Arquivos Anexados
