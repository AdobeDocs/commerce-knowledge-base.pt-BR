---
title: 'Adobe Commerce 2.3.6: ponteiro infinito exibido no salvamento de endereço'
description: Este artigo descreve um problema conhecido do Adobe Commerce 2.3.6, em que o ponteiro de espera é exibido indefinidamente ao salvar um endereço em Minha conta na loja.
exl-id: 63841114-167e-4915-b6ed-ee0ef4eae36e
feature: Shipping/Delivery, Orders, Checkout
role: Developer
source-git-commit: ce377064efabaf09d3856da7c6c5c742a9fdcc2f
workflow-type: tm+mt
source-wordcount: '151'
ht-degree: 0%

---

# Adobe Commerce 2.3.6: ponteiro infinito exibido no salvamento de endereço

Este artigo descreve um problema conhecido do Adobe Commerce 2.3.6, em que o ponteiro de espera é exibido indefinidamente ao salvar um endereço em Minha conta na loja.

## Produtos e versões afetados

* Adobe Commerce 2.3.6 com integração Vertex ativada (somente navegador Firefox)

## Problema

Ao salvar um endereço na seção Minha conta na loja, às vezes o ponteiro de espera é exibido indefinidamente devido a um erro no Vertex core JS.

## Solução alternativa

Solução alternativa: use um navegador alternativo para o Firefox.

O problema foi corrigido no Adobe Commerce 2.3.1.

## Leitura relacionada

* [Atualização de postagem de endereço da mensagem de validação do Endereço Vertex do Adobe Commerce 2.4.1](/help/troubleshooting/miscellaneous/magento-2-4-1-vertex-address-validation-message-post-address-update.md) em nossa base de dados de conhecimento de suporte.
