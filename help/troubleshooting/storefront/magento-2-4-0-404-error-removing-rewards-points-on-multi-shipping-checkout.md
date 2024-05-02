---
title: "Adobe Commerce 2.4.0: erro 404 ao remover pontos de recompensa na finalização de remessa múltipla"
description: Este artigo fornece uma solução alternativa para um problema conhecido no Adobe Commerce 2.4.0 para um erro de página da Web "*404 Não encontrado*" ao remover pontos de recompensa em uma página de check-out de vários envios. Atualmente, na página de checkout de vários envios, ao tentar remover os pontos de premiação usados para pagar um pedido, a página "*404 Não encontrado*" é exibida em vez do cancelamento bem-sucedido dos pontos de premiação. Este problema será resolvido em com uma versão de patch do Adobe Commerce 2.4.1.
exl-id: 59de4b3d-af28-4ae8-8f55-4ec958e6ee8b
feature: B2B, Checkout, Orders, Rewards, Shipping/Delivery, Storefront
role: Admin
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 0%

---

# Adobe Commerce 2.4.0: erro 404 ao remover pontos de recompensa na finalização de remessa múltipla

Este artigo fornece uma solução alternativa para um problema conhecido no Adobe Commerce 2.4.0 para um &quot;*404 Não encontrado*&quot;erro na página da Web ao remover pontos de recompensa em uma página de check-out de vários envios. Atualmente, na página de checkout de vários envios, ao tentar remover pontos de recompensa que eram usados para pagar um pedido, um &quot;*404 Não encontrado* A página &quot; é exibida em vez do cancelamento bem-sucedido de pontos de premiação. Este problema será resolvido em com uma versão de patch do Adobe Commerce 2.4.1.

## Produtos e versões afetados

* Adobe Commerce 2.4.0 (todos os métodos de implantação)

## Problema

<u>Etapas a serem reproduzidas</u>

1. Navegue até a loja e faça logon como cliente.
1. Adicione pelo menos dois produtos à **Carrinho de compras**.
1. Abra o **Minicarrinho**.
1. Clique em **Exibir e editar carrinho** link.
1. Clique em **Fazer Check-out com Vários Endereços** link.
1. Selecione os endereços de entrega no **Vários Endereços para Entrega** página.
1. Clique em **Ir para Informações de Remessa** botão.
1. Selecione o **Taxa Uniforme - Método de Remessa Fixa** para cada endereço.
1. Clique em **Continuar para Informações de Cobrança** botão.
1. Verifique a **Use Seus Pontos De Recompensa** caixa de seleção na **Informações de Cobrança** página.
1. Clique em **Ir para Revisar seu pedido** botão.
1. Clique em **Remover** link para qualquer endereço para remover os pontos de premiação.

<u>Resultados esperados</u>

* A variável **Carrinho de compras** deve ser exibida.
* O &quot;*Você removeu os pontos de premiação deste pedido.* A mensagem &quot; deve ser exibida.

<u>Resultado real</u>

A &quot;*404 Não encontrado* &quot; é exibida.

## Solução alternativa

A solução alternativa é fazer com que o comprador navegue de volta para a **Carrinho** e remova os pontos de premiação do **Carrinho** página da Web. Espera-se que o problema seja corrigido no patch do Adobe Commerce versão 2.4.1, que está programado para ser lançado no quarto trimestre de 2020.

## Leitura relacionada

* [Problema conhecido do Adobe Commerce 2.4.0: a atualização das Atividades do cliente não funciona](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Problema conhecido do Adobe Commerce 2.4.0: exibição de dados de mensagens brutas na loja](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Problema conhecido do Adobe Commerce 2.4.0: as taxas de imposto de exportação não funcionam](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [O administrador B2B do Adobe Commerce 2.4.0 não pode adicionar o produto configurável à cotação](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
* [Problema conhecido do Adobe Commerce 2.4.0: erros de exibição de pedidos](/help/troubleshooting/storefront/magento-2-4-0-known-issue-orders-display-error.md)
