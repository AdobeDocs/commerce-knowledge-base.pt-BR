---
title: Pagamentos com falha de cartão de crédito em um ambiente de Sandbox
description: Este artigo explica por que um cartão de crédito de teste falha em um ambiente de sandbox com APIs do PayPal.
exl-id: 65fd08e0-eefc-47f3-8964-bef3610e6182
feature: Orders, Payments
role: Developer
source-git-commit: 958067830d32b1f10ffa669307ec76d1e14b82a4
workflow-type: tm+mt
source-wordcount: '163'
ht-degree: 0%

---

# Pagamentos com falha de cartão de crédito em um ambiente de Sandbox

Este artigo explica por que um cartão de crédito de teste falha em um ambiente de sandbox com APIs do PayPal.

## Produtos e versões afetados

* Adobe Commerce 2.4.0 - 2.4.4, todas as opções de implantação, com [Serviços de pagamento](https://marketplace.magento.com/magento-payment-services.html)

## Problema

Ao usar um cartão de crédito Visa de teste `4111 1111 1111 1111` do PayPal, às vezes ele falha devido a políticas de fraude do PayPal com o seguinte erro:

```bash
Error happened when processing the request. Please try again later.
```

## Causa

Esse erro é exibido quando o PayPal sinaliza um número de cartão de crédito de teste específico para fraude. Isso acontece porque é um número de cartão de crédito de teste usado por todos no mundo inteiro testando com APIs do PayPal.

## Solução

Use outro cartão de crédito de teste. Para gerar cartões de crédito fictícios, você pode usar para testes:

1. Vá para a página do Portal do Desenvolvedor do PayPal [Gerador de Cartão de Crédito](https://developer.paypal.com/api/rest/sandbox/card-testing/#link-creditcardgenerator).
1. Faça logon no Painel do Portal do Desenvolvedor do PayPal.
1. Gerar um cartão de crédito de teste.
