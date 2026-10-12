---
title: 'Problema conhecido do Adobe Commerce 2.4.0: páginas em branco de mensagens no site do Klarna'
description: Este artigo descreve um problema conhecido do Adobe Commerce 2.4.0 com o método de pagamento Klarna, em que ativar mensagens no site do Klarna sem especificar um tema de design resulta na não exibição correta das páginas de produto na loja (as páginas de produto aparecem em branco).
exl-id: f0f9edfc-eaad-4947-9200-41e217bfbe84
feature: Orders, Payments
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 3dcbfa9e-51f8-569c-a0e4-7f59098f730f
    internal-label: Payments
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '204'
ht-degree: 0%
---
# Problema conhecido do Adobe Commerce 2.4.0: páginas em branco de mensagens no site do Klarna

Este artigo descreve um problema conhecido do Adobe Commerce 2.4.0 com o método de pagamento Klarna, em que ativar mensagens no site do Klarna sem especificar um tema de design resulta na não exibição correta das páginas de produto na loja (as páginas de produto aparecem em branco).

## Produtos e versões afetados

* Adobe Commerce no local 2.4.0
* Adobe Commerce na infraestrutura em nuvem 2.4.0

<u>Pré-requisitos:</u> o método de pagamento Klarna está habilitado.

<u>Etapas a serem reproduzidas:</u>

1. No Administrador do Commerce, vá para **Lojas** > **Configuração** > **Vendas** > **Métodos de Pagamento** > **Klarna** > **Mensagens Klarna No Site**.
1. Definir **Habilitar** para *Sim*.
1. Deixe o campo **Tema de design** em branco.
1. Salve a configuração clicando em **Salvar Configuração**.
1. Acesse a loja e navegue até qualquer página de produto.

<u>Resultado esperado:</u>

A página é carregada com sucesso com o tema de design padrão aplicado às mensagens no site do Klarna.

<u>Resultado real:</u>

Uma página em branco é exibida.

## Solução

Se estiver habilitando as mensagens no site do Klarna, sempre verifique se o campo **Tema de design** não está em branco.
