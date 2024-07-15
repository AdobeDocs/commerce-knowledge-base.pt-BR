---
title: Erro de nível máximo de aninhamento de função xdebug de instalação
description: Este artigo fornece uma correção para o erro de nível de aninhamento de função máxima xdebug durante a instalação.
exl-id: 1f64a9bb-59a7-41df-92a4-890d9d32bcbe
feature: Install
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
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
