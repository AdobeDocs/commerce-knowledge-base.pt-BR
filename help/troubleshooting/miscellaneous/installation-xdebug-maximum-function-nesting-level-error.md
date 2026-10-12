---
title: Erro de nível máximo de aninhamento de função xdebug de instalação
description: Este artigo fornece uma correção para o erro de nível de aninhamento de função máxima xdebug durante a instalação.
exl-id: 1f64a9bb-59a7-41df-92a4-890d9d32bcbe
feature: Install
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 6388cf7b-8a81-5248-a1e4-7bb57bbe250f
    internal-label: Install
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '104'
ht-degree: 0%
---
# Erro de nível máximo de aninhamento de função xdebug de instalação

Este artigo fornece uma correção para o erro de nível de aninhamento de função máxima xdebug durante a instalação.

## Detalhes

Durante a instalação do Adobe Commerce, uma mensagem semelhante à seguinte é exibida:

`PHP Fatal error: Maximum function nesting level of '100' reached, aborting! in <path>/ClassLoader.php`

É altamente recomendável que você NÃO USE o `xdebug` em um ambiente de Produção!

## Solução

Há um problema conhecido com o `xdebug` que pode afetar as instalações do Adobe Commerce ou o acesso ao Administrador da loja ou do Commerce após a instalação.

Para obter detalhes, consulte [Problema conhecido com xdebug](/help/troubleshooting/miscellaneous/known-issues-that-affect-installation.md) em nossa knowledge base de suporte.
