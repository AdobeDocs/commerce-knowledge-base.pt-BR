---
title: "Adobe Commerce 2.3.7-p1 problema conhecido: total de pedido desatualizado para PayPal"
description: "Este artigo fornece um patch para um problema conhecido no Adobe Commerce 2.3.7-p1: ao usar o Check-out do PayPal mais de uma vez, os clientes obtêm o produto solicitado anteriormente no carrinho, em vez do novo que estão tentando solicitar."
exl-id: ceb8f7ad-0cf7-4d42-aded-25d1dd947f5b
feature: Orders, Payments
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 0%

---

# Problema conhecido do Adobe Commerce 2.3.7-p1: total de pedidos desatualizado para PayPal

Este artigo fornece um patch para um problema conhecido no Adobe Commerce 2.3.7-p1: ao usar o Check-out do PayPal mais de uma vez, os clientes obtêm o produto solicitado anteriormente no carrinho, em vez do novo que estão tentando solicitar.
Você pode baixar o patch neste artigo e ele também está disponível através da Ferramenta de patches de qualidade (QPT).

## Versões afetadas

* Adobe Commerce (todas as opções de implantação) 2.3.7-p1
* Magento Open Source 2.3.7-p1

## Problema

Ao fazer um pedido usando o método de pagamento PayPal Express Checkout, o produto comprado anteriormente é adicionado ao pedido em vez do produto real.

<u>Etapas a serem reproduzidas:</u>

1. Na loja, adicione qualquer produto ao carrinho (produto A, preço US$ 50).
1. Clique no link do carrinho para abrir o carrinho.
1. Clique no botão **Check-out do PayPal**.
1. Use suas credenciais do PayPal para fazer logon no PayPal e enviar o pagamento.
1. Concluir o posicionamento do pedido no lado do armazenamento.
1. Retorne ao catálogo e adicione um produto diferente (produto B, preço US$ 100) ao carrinho.
1. Clique no link do carrinho para abrir o carrinho.
1. Clique no botão **Check-out do PayPal**.

<u>Resultado real:</u>

O preço do produto no carrinho é de US$ 50 em vez de US$ 100.<br/>
No lado da loja, o pedido contém o produto A em vez do produto B.

<u>Resultado esperado:</u>

O produto B é adicionado ao pedido.

## Solução

Aplique o patch fornecido neste artigo.

## Correção

Use o link a seguir para baixar um arquivo .zip que contém o patch: [MC42674-composer.patch.zip](assets/MC42674-composer.patch.zip).

### Versões compatíveis do Adobe Commerce

* Adobe Commerce (todas as opções de implantação) 2.3.7-p1

## Como aplicar os patches

1. Descompacte o arquivo .zip baixado.
1. Consulte [Como aplicar um patch de compositor fornecido pelo Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) para obter mais instruções.
