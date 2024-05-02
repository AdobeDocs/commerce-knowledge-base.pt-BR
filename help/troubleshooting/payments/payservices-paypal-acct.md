---
title: Conta de sandbox do PayPal não verificada
description: Este artigo explica por que a conta de sandbox do PayPal para Serviços de pagamento pode não ser verificada, impedindo que você conclua a integração da sandbox.
exl-id: 05ce130d-6dfe-4834-bdfc-837902100118
feature: Customer Service, Orders, Payments
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 0%

---

# Conta de sandbox do PayPal não verificada

Este artigo explica por que a conta de sandbox do PayPal para Serviços de pagamento pode não ser verificada, impedindo que você conclua a integração da sandbox.

## Produtos e versões afetados

* [Payment Services](https://marketplace.magento.com/magento-payment-services.html) O agora é compatível com as versões 2.4.0 a 2.4.4 do Adobe Commerce.

## Problema

Nosso [documentação de integração](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/onboard.html) O instrui você a se inscrever em uma conta do PayPal, fazer logon na conta de desenvolvedores do PayPal e criar uma conta de sandbox. Se você optar por criar uma nova conta durante a integração na janela pop-up de integração do PayPal, o PayPal não poderá verificar sua conta de sandbox e você não poderá concluir a integração.

<u>Etapas a serem reproduzidas</u>:

1. Você [instalar Serviços de pagamento](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/install.html) e [configurar os serviços da Commerce](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/connect.html#configure-commerce-services).
1. Você navega até **Payment Services** em Admin e [iniciar integração de sandbox](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/onboard.html).
1. No pop-up de integração do PayPal exibido, você cria uma nova conta Comercial (em vez de [fazer logon com uma conta de sandbox do PayPal criada anteriormente](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/sandbox.html#test-in-sandbox-environment) durante a integração.
1. Você concluiu com êxito a integração do PayPal.
1. Você verá uma notificação no Administrador de que seus pagamentos de sandbox estão pendentes e que você deve confirmar seu endereço de email no PayPal para concluir a integração.

   Você não recebeu um email de confirmação porque o PayPal não pôde verificar seu endereço de email.

## Causa

O PayPal não poderá verificar sua conta de sandbox e você não poderá concluir a integração da sandbox (o que significa que não é possível aceitar pagamentos ou testar seu modo de sandbox) se criar sua conta de sandbox antes da conta do PayPal.

## Solução

1. Uso de uma conta de sandbox criada no [Desenvolvedor do PayPal](https://developer.paypal.com/docs/api-basics/sandbox/accounts/#create-a-business-sandbox-account) Portal.
1. Clique em [redefinir sandbox](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/sandbox.html#test-in-sandbox-environment) e reinicie a integração da sandbox.
1. [Entrar em contato com o suporte](mailto:payment-services-support@adobe.com) caso não consiga aliviar os problemas de sua conta para que possa retomar a integração e aceitar pagamentos.
