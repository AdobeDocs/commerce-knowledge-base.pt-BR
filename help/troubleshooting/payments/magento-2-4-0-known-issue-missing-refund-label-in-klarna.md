---
title: 'Problema conhecido do Adobe Commerce 2.4.0: falta o rótulo "Reembolso" no Klarna'
description: Este artigo fornece uma solução alternativa para um problema conhecido no Admin para um rótulo **Reembolso** ausente no Klarna VBE (Vendor Bundled Extension). Quando estiver no portal Klarna realizando um reembolso, o rótulo **Reembolso** não é exibido ao lado do produto agrupado que foi reembolsado.
exl-id: f08039b2-7f8b-481e-8ec8-1659e227744f
feature: B2B, Orders, Payments
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 3dcbfa9e-51f8-569c-a0e4-7f59098f730f
    internal-label: Payments
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%
---
# Problema conhecido do Adobe Commerce 2.4.0: falta o rótulo &quot;Reembolso&quot; no Klarna

Este artigo fornece uma solução alternativa para um problema conhecido no Admin para um rótulo **Reembolso** ausente no Klarna VBE (Vendor Bundled Extension). Quando estiver no portal Klarna realizando um reembolso, o rótulo **Reembolso** não será exibido ao lado do produto Empacotado que foi reembolsado.

## Produtos e versões afetados

* Adobe Commerce no local 2.4.0
* Adobe Commerce na infraestrutura em nuvem 2.4.0

## Problema

<u>Pré-requisitos:</u>

* O Klarna está ativado.
* Um produto agrupado é criado.

<u>Etapas a serem reproduzidas</u>

1. Vá para o front-end do Adobe Commerce e adicione um produto incluído ao **carrinho**.
1. Navegue até check-out.
1. Insira as informações do consumidor no check-out e clique em **Avançar**.
1. Selecione a **opção KP** e clique em **Fazer Pedido**.
1. Vá para **Admin** > **Vendas** > **Pedidos**.
1. Abra o pedido.
1. Criar fatura para o produto.
1. Vá para **Faturas** > **Selecionar fatura** > Clique em **Memorando de Crédito** > Clique em **Reembolso** (Não **Reembolso Offline**).
1. Vá para o portal Klarna.
1. Abra o pedido.
1. O rótulo **Reembolso** está presente.

<u>Resultado esperado</u>

No portal Klarna, o rótulo **Reembolso** é exibido ao lado do produto que foi reembolsado.

<u>Resultado real</u>

No portal Klarna, o rótulo **Reembolso** não é exibido ao lado do produto reembolsado.

## Solução alternativa

A solução alternativa para esse problema é ignorar o rótulo **Reembolso** ausente no portal Klarna para produtos agrupados reembolsados. O reembolso ocorreu, mesmo que o rótulo **Reembolso** não tenha sido exibido. O problema deve ser corrigido no Adobe Commerce 2.4.1, com lançamento previsto para o quarto trimestre de 2020.

## Leituras relacionadas em nossa base de conhecimento de suporte:

* [Problema conhecido do Adobe Commerce 2.4.0: os métodos de pagamento do Braintree não são exibidos na finalização de vários endereços](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Problema conhecido do Adobe Commerce 2.4.0: mensagem de erro que seleciona o método de pagamento local exibido para alguns países durante a finalização da compra](/help/troubleshooting/payments/magento-2-4-0-checkout-error-selecting-local-payments.md)
