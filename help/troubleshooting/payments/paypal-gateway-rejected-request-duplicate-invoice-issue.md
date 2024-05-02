---
title: Solicitação rejeitada do gateway do PayPal - problema de fatura duplicado
description: Este artigo fornece uma correção para a solicitação rejeitada do gateway do PayPal - problema de fatura duplicado.
exl-id: b6c4ede1-97a5-4db3-9b05-ab979cf809b3
feature: Invoices, Orders, Payments
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 0%

---

# Solicitação rejeitada do gateway do PayPal - problema de fatura duplicado

Este artigo fornece uma correção para a solicitação rejeitada do gateway do PayPal - problema de fatura duplicado.

Ao enviar o pagamento, os Clientes podem ver um erro para uma fatura duplicada:

>O gateway do PayPal rejeitou a solicitação. Já foi feito o pagamento para esta ID de fatura (\#10412: fatura duplicada)

O problema ocorre quando faturas com as mesmas IDs são enviadas para o PayPal várias vezes.

Para resolver o problema, permita vários pagamentos por ID de fatura nas Preferências de Recebimento de Pagamento do PayPal. Quando alterado, o PayPal aceita pagamentos sem mensagens de erro, mesmo para faturas com IDs duplicadas.

## Versões afetadas

* Adobe Commerce no local, todas as versões
* Adobe Commerce na infraestrutura em nuvem, todas as versões

## Problema

Ao enviar o pagamento, os clientes verão a mensagem de erro:

```
... main.CRITICAL: Exception message: PayPal gateway has rejected request. Payment has already been made for this InvoiceID (#10412: Duplicate invoice).
```

O PayPal não pode processar o pagamento e concluir o pedido.

## Causa

A mensagem de erro é exibida quando faturas com a mesma ID são enviadas ao PayPal várias vezes.

Isso pode acontecer ao usar as mesmas credenciais em vários sites do Adobe Commerce (mesmo nos ambientes Local e de armazenamento temporário). Cenários específicos podem ser os seguintes:

* Várias lojas enviam faturas para o PayPal e usam as mesmas IDs de fatura
* Um novo armazenamento envia uma fatura com uma ID que foi enviada anteriormente por um armazenamento antigo

Por padrão, o PayPal não permite o processamento da mesma fatura duas vezes.

## Solução

Altere seu perfil do PayPal para permitir vários pagamentos por ID de fatura. Você precisa fazer essas alterações por meio do PayPal.

1. Faça logon em sua conta em [https://www.paypal.com](https://www.paypal.com/).
1. Clique em **Perfil** > **Perfil e configurações** (canto superior direito).
1. Ir para **Minhas ferramentas de vendas**.
1. Navegue até **Receber e gerenciar meu risco** > **Bloquear pagamentos** e clique em **Atualizar**.
1. **Preferências de venda**, clique em **Preferências de Recebimento de Pagamento**.
1. Em **Bloquear pagamentos acidentais**, escolha **Não, permitir vários pagamentos por ID de fatura**.    ![paypal_allow_multiple_payments_per_Invoice_id.png](assets/paypal_allow_multiple_payments_per_invoice_id.png)
1. Role para baixo e clique em **Salvar**.

## Mais informações

* [Bloquear pagamentos acidentais](https://developer.paypal.com/docs/admin/setup-account/#block-accidental-payments) nos Documentos do desenvolvedor do PayPal.
* Pagamentos do PayPal em nosso guia do usuário:
   * [Check-out do PayPal Express](/docs/commerce-admin/stores-sales/payments/paypal/paypal-express-checkout.html)
   * [Outras soluções do PayPal](/docs/commerce-admin/stores-sales/payments/paypal/paypal.html)
* Em nossa documentação do desenvolvedor:
   * [Configurar métodos de pagamento do PayPal para Adobe Commerce na infraestrutura em nuvem](/docs/commerce-cloud-service/user-guide/configure-store/paypal.html)
   * [Integrações de Pagamentos](https://developer.adobe.com/commerce/php/development/payments-integrations/)
