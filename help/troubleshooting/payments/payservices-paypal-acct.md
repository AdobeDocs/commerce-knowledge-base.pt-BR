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

* [Os Serviços de Pagamento](https://marketplace.magento.com/magento-payment-services.html) agora são compatíveis com as versões 2.4.0 a 2.4.4 do Adobe Commerce.

## Problema

Nossa [documentação de integração](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/onboard.html) instrui você a se inscrever em uma conta do PayPal, fazer logon na conta de desenvolvedores do PayPal e criar uma conta de sandbox. Se você optar por criar uma nova conta durante a integração na janela pop-up de integração do PayPal, o PayPal não poderá verificar sua conta de sandbox e você não poderá concluir a integração.

<u>Etapas a serem reproduzidas</u>:

1. Você [instala Serviços de Pagamento](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/install.html) e [configura os Serviços da Commerce](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/connect.html#configure-commerce-services).
1. Você navega até **Serviços de pagamento** no Administrador e [inicia a integração da sandbox](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/onboard.html).
1. Na janela pop-up de integração do PayPal exibida, você cria uma nova Conta comercial (em vez de [fazer logon com uma conta de sandbox do PayPal](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/sandbox.html#test-in-sandbox-environment) criada anteriormente) durante a integração.
1. Você concluiu com êxito a integração do PayPal.
1. Você verá uma notificação no Administrador de que seus pagamentos de sandbox estão pendentes e que você deve confirmar seu endereço de email no PayPal para concluir a integração.

   Você não recebeu um email de confirmação porque o PayPal não pôde verificar seu endereço de email.

## Causa

O PayPal não poderá verificar sua conta de sandbox e você não poderá concluir a integração da sandbox (o que significa que não é possível aceitar pagamentos ou testar seu modo de sandbox) se criar sua conta de sandbox antes da conta do PayPal.

## Solução

1. Usando uma conta de sandbox criada no Portal [PayPal Developer](https://developer.paypal.com/docs/api-basics/sandbox/accounts/#create-a-business-sandbox-account).
1. Clique em [redefinir sandbox](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/sandbox.html#test-in-sandbox-environment) e reinicie a integração da sandbox.
1. [Contate o suporte](mailto:payment-services-support@adobe.com) se não conseguir resolver seus problemas de conta para que você possa retomar a integração e aceitar pagamentos.
