---
title: "Problema conhecido do Adobe Commerce 2.4.0: páginas em branco de mensagens no site do Klarna"
description: Este artigo descreve um problema conhecido do Adobe Commerce 2.4.0 com o método de pagamento Klarna, em que ativar mensagens no site do Klarna sem especificar um tema de design resulta na não exibição correta das páginas de produto na loja (as páginas de produto aparecem em branco).
exl-id: f0f9edfc-eaad-4947-9200-41e217bfbe84
feature: Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '202'
ht-degree: 0%

---

# Problema conhecido do Adobe Commerce 2.4.0: páginas em branco de mensagens no site do Klarna

Este artigo descreve um problema conhecido do Adobe Commerce 2.4.0 com o método de pagamento Klarna, em que ativar mensagens no site do Klarna sem especificar um tema de design resulta na não exibição correta das páginas de produto na loja (as páginas de produto aparecem em branco).

## Produtos e versões afetados

* Adobe Commerce no local 2.4.0
* Adobe Commerce na infraestrutura em nuvem 2.4.0

<u>Pré-requisitos:</u> O método de pagamento Klarna está habilitado.

<u>Etapas a serem reproduzidas:</u>

1. No Administrador do Commerce, acesse **Lojas** > **Configuração** > **Vendas** > **Métodos de pagamento** > **Klarna** > **Mensagens no site do Klarna**.
1. Definir **Ativar** para *Sim*.
1. Deixe a **Tema de design** campo em branco.
1. Salve a configuração clicando em **Salvar configuração**.
1. Acesse a loja e navegue até qualquer página de produto.

<u>Resultado esperado:</u>

A página é carregada com sucesso com o tema de design padrão aplicado às mensagens no site do Klarna.

<u>Resultado real:</u>

Uma página em branco é exibida.

## Solução

Se ativar as mensagens no site do Klarna, sempre verifique se **Tema de design** não está em branco.
