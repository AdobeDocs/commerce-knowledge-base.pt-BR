---
title: Falha na instalação do Adobe Commerce 2.4.0 com cache de lojas desatualizado
description: 'Este artigo fornece uma solução para o problema em que a instalação do Adobe Commerce 2.4.0 falha com a mensagem de erro: *O site padrão não está definido. Defina o site e tente novamente.* exibido no console.'
exl-id: 0680199b-7e47-4a8c-91fe-9f6c32839a0e
feature: B2B, Cache, Console, Install, Upgrade
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 6388cf7b-8a81-5248-a1e4-7bb57bbe250f
    internal-label: Install
  - id: a8ae7a5a-6cdc-5922-bd0d-6feb44b04984
    internal-label: Upgrade
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
  - id: c4af0798-d497-5e6b-8380-19812c26d00a
    internal-label: Console
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 0%
---
# Falha na instalação do Adobe Commerce 2.4.0 com cache de lojas desatualizado

Este artigo fornece uma solução para o problema em que a instalação do Adobe Commerce 2.4.0 falha com a mensagem de erro: *O site padrão não está definido. Defina o site e tente novamente.* exibido no console.

## Produtos e versões afetados

* Adobe Commerce na infraestrutura em nuvem 2.4.0
* Adobe Commerce no local 2.4.0

## Problema

<u>Pré-requisitos:</u>
Uma extensão de terceiros com dependências em APIs para o módulo Store em comandos CLI está configurada conforme exigido em `composer.json`. Isso faz com que a instalação do Adobe Commerce 2.4.0 falhe com uma mensagem de erro: *O site padrão não está definido. Defina o site e tente novamente.* exibido no console.

## Causa

O problema aparece para as extensões de terceiros que têm dependências de armazenamentos em seus comandos CLI. Um deles é o Amazon Sales Channels.

## Solução

Antes da instalação do Adobe Commerce 2.4.0, os comerciantes precisam:

1. Remova essas extensões de terceiros de `composer.json`.
1. Instalar o Adobe Commerce sem extensões.
1. Adicione as extensões após a instalação.

O problema será corrigido no escopo da versão 2.4.1 do.

## Leituras relacionadas em nossa base de conhecimento de suporte:

* [Problema conhecido do Adobe Commerce 2.4.0: falta o rótulo &quot;Reembolso&quot; no Klarna](/help/troubleshooting/payments/magento-2-4-0-known-issue-missing-refund-label-in-klarna.md)
* [Adobe Commerce 2.4.0, 2.4.1: Ativar problema de fatura parcial do Braintree Venmo](/help/troubleshooting/payments/magento-2-4-0-2-4-1-enable-braintree-venmo-partial-invoice-issue.md)
* [Problema conhecido do Adobe Commerce 2.4.0: mensagem de erro que seleciona o método de pagamento local exibido para alguns países durante a finalização da compra](/help/troubleshooting/payments/magento-2-4-0-checkout-error-selecting-local-payments.md)
* [Problema conhecido do Adobe Commerce 2.4.0: Pagamento do Amazon ativado, métodos de pagamento ausentes ao retornar ao checkout padrão usado](/help/troubleshooting/payments/magento-2-4-0-known-issue-amazon-pay-no-payment-methods.md)
* [Problema conhecido do Adobe Commerce 2.4.0: os métodos de pagamento do Braintree não são exibidos na finalização de vários endereços](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)

