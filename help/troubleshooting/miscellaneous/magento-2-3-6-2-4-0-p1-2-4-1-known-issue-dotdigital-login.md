---
title: "Adobe Commerce 2.3.6, 2.4.0-p1, 2.4.1 problema conhecido: dotdigital login"
description: Este artigo descreve um problema conhecido do Adobe Commerce 2.3.6, 2.4.0-p1 e 2.4.1 em que é impossível fazer logon no [dotdigital](https://dotdigital.com/) por meio do Painel de administração quando a conta dotdigital está ativada.
exl-id: 427d895c-8c03-4ced-813a-eeaa67f1d1f0
feature: Configuration
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 0%

---

# Adobe Commerce 2.3.6, 2.4.0-p1, 2.4.1 problema conhecido: dotdigital login

Este artigo descreve um problema conhecido do Adobe Commerce 2.3.6, 2.4.0-p1 e 2.4.1 em que é impossível fazer logon no [dotdigital](https://dotdigital.com/) por meio do Painel de Administração quando a conta dotdigital está habilitada.

## Produtos e versões afetados

* Adobe Commerce na infraestrutura em nuvem e Adobe Commerce no local 2.3.6 (somente navegador Safari)
* Adobe Commerce na infraestrutura em nuvem e Adobe Commerce no local 2.4.0-p1 (somente navegador Safari)
* Adobe Commerce na infraestrutura em nuvem e Adobe Commerce no local 2.4.1 (somente navegador Safari)

## Problema

<u>Pré-requisitos</u>:

1. conta dotdigital existe.
1. Existem credenciais de API dotdigital válidas no Adobe Commerce.

<u>Etapas a serem reproduzidas</u>:

1. Vá para **Lojas** > **Configuração** > **DOTDIGITAL** > **Configurações de Chat** > **Habilitadas** está definido como *Sim.*
1. Clique em **Configurar** em **Configurar Widget de Chat** ou **Configurar equipes de chat**.

<u>Resultados esperados</u>:

A página de configurações do chat deve abrir com êxito através do Painel de administração.

<u>Resultados reais</u>:

Não é possível fazer logon no dotdigital.

## Solução

Solução alternativa: use um navegador alternativo para o Safari para essa situação específica.

## Leitura relacionada

[Problema conhecido do Adobe Commerce 2.4.1 - O endereço Vertex não está sendo validado com endereços de remessa/cobrança diferentes](/help/troubleshooting/miscellaneous/magento-2-4-1-vertex-address-validation-message-post-address-update.md) em nossa base de dados de conhecimento de suporte.
