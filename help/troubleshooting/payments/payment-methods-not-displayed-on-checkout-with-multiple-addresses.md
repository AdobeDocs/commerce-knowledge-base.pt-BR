---
title: Métodos de pagamento não exibidos no check-out com vários endereços
description: Este artigo explica que a maioria dos métodos de pagamento não é exibida no check-out quando vários endereços de envio são especificados, pois a funcionalidade é implementada apenas para o Cybersource.
exl-id: 68a9ee77-d0ef-43c5-9667-6d099b797666
feature: Checkout, Orders, Payments, Shipping/Delivery
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 8cd50456-5eb0-5364-922a-f14161feb828
    internal-label: Checkout
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 3dcbfa9e-51f8-569c-a0e4-7f59098f730f
    internal-label: Payments
  - id: 04d3134c-2afb-5bd7-ac14-e19fa935e848
    internal-label: Shipping/Delivery
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '262'
ht-degree: 0%
---
# Métodos de pagamento não exibidos no check-out com vários endereços

Este artigo explica que a maioria dos métodos de pagamento não é exibida no check-out quando vários endereços de envio são especificados, pois a funcionalidade é implementada apenas para o Cybersource.

## Produtos e versões afetados

* Adobe Commerce no local 2.x.x
* Adobe Commerce na infraestrutura em nuvem 2.x.x

>[!NOTE]
>
>A integração de pagamento principal do Adobe Commerce Cybersource está obsoleta desde a versão 2.3.3 e será completamente removida na versão 2.4.0. Em vez disso, use a [extensão oficial](https://marketplace.magento.com/cybersource-global-payment-management.html) do marketplace.

## Problema

<u>Pré-requisitos</u>: no Commerce Admin, habilite e configure os métodos de pagamento do PayPal e do Cybersource e habilite o Multisdelivery para sua loja.

<u>Etapas a serem reproduzidas</u>:

1. Na loja, adicione vários produtos ao carrinho.
1. Vá para a página do carrinho de compras.
1. Clique em **Fazer Check-out com Vários Endereços**.
1. Faça logon ou crie uma conta.
1. Divida os produtos entre os endereços na página Enviar para Vários Endereços.
1. Clique em **Ir para Informações de Envio**.
1. Selecione métodos de entrega para cada entrega.
1. Clique em **Continuar para as Informações de Cobrança**.

<u>Resultado esperado</u>: PayPal e Cybersource estão disponíveis como opções de pagamento.

<u>Resultado real</u>: somente Cybersource aparece como opção de pagamento disponível.

## Causa

Atualmente, o Cybersource é o único método de pagamento ao vivo compatível para check-out de vários envios, a partir da versão 2.2.4. O suporte para envio múltiplo provavelmente será criado para cada método de pagamento, um por um. Não é possível fornecer datas exatas ou números de versão no momento.
