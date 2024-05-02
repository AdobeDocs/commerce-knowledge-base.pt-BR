---
title: Métodos de pagamento não exibidos no check-out com vários endereços
description: Este artigo explica que a maioria dos métodos de pagamento não é exibida no check-out quando vários endereços de envio são especificados, pois a funcionalidade é implementada apenas para o Cybersource.
exl-id: 68a9ee77-d0ef-43c5-9667-6d099b797666
feature: Checkout, Orders, Payments, Shipping/Delivery
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 0%

---

# Métodos de pagamento não exibidos no check-out com vários endereços

Este artigo explica que a maioria dos métodos de pagamento não é exibida no check-out quando vários endereços de envio são especificados, pois a funcionalidade é implementada apenas para o Cybersource.

## Produtos e versões afetados

* Adobe Commerce no local 2.x.x
* Adobe Commerce na infraestrutura em nuvem 2.x.x

>[!NOTE]
>
>A integração de pagamento principal do Adobe Commerce Cybersource está obsoleta desde a versão 2.3.3 e será completamente removida na versão 2.4.0. Use o [extensão oficial](https://marketplace.magento.com/cybersource-global-payment-management.html) do marketplace em vez disso.

## Problema

<u>Pré-requisitos</u>: no Commerce Admin, ative e configure os métodos de pagamento do PayPal e do Cybersource e ative o Multidelivery para sua loja.

<u>Etapas a serem reproduzidas</u>:

1. Na loja, adicione vários produtos ao carrinho.
1. Vá para a página do carrinho de compras.
1. Clique em **Fazer Check-out com Vários Endereços**.
1. Faça logon ou crie uma conta.
1. Divida os produtos entre os endereços na página Enviar para Vários Endereços.
1. Clique em **Ir para Informações de Remessa**.
1. Selecione métodos de entrega para cada entrega.
1. Clique em **Continuar para Informações de Cobrança**.

<u>Resultado esperado</u>: PayPal e Cybersource estão disponíveis como opções de pagamento.

<u>Resultado real</u>: Somente o Cybersource aparece como a opção de pagamento disponível.

## Causa

Atualmente, o Cybersource é o único método de pagamento ao vivo compatível para check-out de vários envios, a partir da versão 2.2.4. O suporte para envio múltiplo provavelmente será criado para cada método de pagamento, um por um. Não é possível fornecer datas exatas ou números de versão no momento.
