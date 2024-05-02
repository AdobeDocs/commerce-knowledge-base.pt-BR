---
title: "Adobe Commerce 2.4.0 B2B: lógica de ordem de compra incorreta quando o desconto expirou"
description: Este artigo fornece uma correção para a emissão conhecida de um desconto de ordem de compra (OC) que não está sendo aplicado no Adobe Commerce 2.4.0 B2B. Se a OC foi colocada com um código de desconto que expirou enquanto a OC estava no processo de aprovação, a ordem aprovada não refletirá o desconto.
exl-id: 3ef41655-c31e-4e9c-8985-fa1b4fd53170
feature: B2B, Orders, Payments, Personalization, Purchase Orders
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 0%

---

# Adobe Commerce 2.4.0 B2B: lógica de ordem de compra incorreta quando o desconto expirou

Este artigo fornece uma correção para a emissão conhecida de um desconto de ordem de compra (OC) que não está sendo aplicado no Adobe Commerce 2.4.0 B2B. Se a OC foi colocada com um código de desconto que expirou enquanto a OC estava no processo de aprovação, a ordem aprovada não refletirá o desconto.

## Produtos e versões afetados

* Adobe Commerce na infraestrutura em nuvem 2.4.0
* Adobe Commerce no local 2.4.0

## Problema

<u>Pré-requisitos</u>: um cupom de desconto é criado e existem regras de aprovação que impedem o processamento automático de OCs.

<u>Etapas a serem reproduzidas:</u>

1. Colocar uma OC com desconto aplicado.
1. Desativar o cupom de desconto.
1. Aprovar OC como gerente.
1. Verifique a ordem criada como resultado.

<u>Resultado esperado:</u>

O pedido é criado com um total descontado.

<u>Resultado real:</u>

O pedido é criado para o valor total.

## Solução

Aplique o patch fornecido neste artigo.

## Correção

O patch está anexado a este artigo. Para baixá-lo, role para baixo até o final do artigo e clique no nome do arquivo ou clique no link a seguir:

[B2B-709-composer.patch](assets/B2B-709-composer.patch.zip)

O patch também está disponível para download no, `.git` e `.composer` , formatos em [Downloads da Adobe Commerce](https://magento.com/tech-resources/download) página, em **Correções** na navegação de coluna à esquerda. Procure o patch XXX.

## Como aplicar o patch

Consulte [Como aplicar um patch de compositor fornecido pelo Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) na nossa base de conhecimento de suporte para obter instruções.
