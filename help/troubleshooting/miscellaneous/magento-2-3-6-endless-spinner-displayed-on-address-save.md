---
title: 'Adobe Commerce 2.3.6: ponteiro infinito exibido no salvamento de endereço'
description: Este artigo descreve um problema conhecido do Adobe Commerce 2.3.6, em que o ponteiro de espera é exibido indefinidamente ao salvar um endereço em Minha conta na loja.
exl-id: 63841114-167e-4915-b6ed-ee0ef4eae36e
feature: Shipping/Delivery, Orders, Checkout
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '173'
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

* [Endereços diferentes não permitidos ao desmarcar &#39;Meus endereços de cobrança e de remessa são iguais&#39; usando a Limpeza VertexAddress](/help/troubleshooting/miscellaneous/vertex-address-cleansing-different-addresses-not-allowed.md) em nossa base de dados de conhecimento de suporte.
* [Atualização de postagem de endereço da mensagem de validação do Endereço Vertex do Adobe Commerce 2.4.1](/help/troubleshooting/miscellaneous/magento-2-4-1-vertex-address-validation-message-post-address-update.md) em nossa base de dados de conhecimento de suporte.
