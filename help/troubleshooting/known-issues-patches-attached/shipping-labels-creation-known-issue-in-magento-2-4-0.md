---
title: Problema conhecido na criação de etiquetas de remessa no Adobe Commerce 2.4.0
description: Este artigo fornece um patch para um problema conhecido do Adobe Commerce 2.4.0, em que um rótulo de remessa não pode ser criado.
exl-id: 722689d9-0c90-4a9d-8449-e93c6585b7c3
feature: Orders, Shipping/Delivery
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%

---

# Problema conhecido na criação de etiquetas de remessa no Adobe Commerce 2.4.0

Este artigo fornece um patch para um problema conhecido do Adobe Commerce 2.4.0, em que um rótulo de remessa não pode ser criado.

## Produtos e versões afetados

* Adobe Commerce no local 2.4.0
* Adobe Commerce na infraestrutura em nuvem 2.4.0

## Problema

<u>Pré-requisitos</u>: criar um pedido usando o método de envio FedEx, DHL, UPS ou USPS.

### Cenário 1: criar uma etiqueta ao adicionar uma remessa

<u>Etapas a serem reproduzidas:</u>

1. Abra o pedido feito no Administrador em **Vendas** > **Pedidos**.
1. Clique no botão **Enviar**. A página **Nova remessa** é aberta.

<u>Resultado esperado:</u>

A caixa de seleção **Criar etiqueta de remessa** é exibida na parte inferior da página.

<u>Resultado real:</u>

A caixa de seleção **Criar etiqueta de remessa** não é exibida.

### Cenário 2: criar uma etiqueta para remessa existente

<u>Etapas a serem reproduzidas:</u>

1. Abra o pedido feito no Administrador em **Vendas** > **Pedidos**.
1. Clique no botão **Enviar**. A página **Nova remessa** é aberta.
1. Clique no botão **Enviar Remessa**. Uma entrega é criada.
1. Abra a entrega recém-criada.
1. Clique no botão **Criar etiqueta de remessa**. A caixa de diálogo **Criar Pacotes** é aberta.

<u>Resultado esperado:</u>

O botão **Adicionar Produtos ao Pacote** na janela modal **Criar Pacotes** exibe campos com itens de pedido.

<u>Resultado real:</u>

A janela modal **Criar Pacotes** não é exibida corretamente. Não é possível adicionar itens de pedido à remessa.

## Solução

Aplique o patch fornecido neste artigo.

## Correção

O patch está anexado a este artigo. Para baixá-lo, role para baixo até o final do artigo e clique no nome do arquivo ou clique no link a seguir:

[MC-35514-2.4.0-CE-composer-2.patch](assets/MC-35514-2.4.0-CE-composer-2.patch.zip)

O patch também está disponível para download nos formatos `.git` e `.composer`, na página [Downloads da Adobe Commerce](https://magento.com/tech-resources/download), em **Patches**, na navegação de coluna à esquerda. Procure o patch MC-35514.

### Versões compatíveis do Adobe Commerce:

A correção foi criada para:

* Adobe Commerce na infraestrutura em nuvem versão 2.4.0
* Adobe Commerce no local versão 2.4.0

## Como aplicar o patch

Consulte [Como aplicar um patch de compositor fornecido pelo Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) para obter instruções.

## Arquivos Anexados
