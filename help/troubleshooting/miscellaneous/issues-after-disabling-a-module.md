---
title: Problemas após desabilitar um módulo
description: Este artigo fornece uma solução para problemas de funcionalidade do módulo após desativar a saída do módulo no Commerce Admin.
exl-id: 517f6993-f09e-4a94-8c57-175ecf9a98a8
feature: Extensions
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '151'
ht-degree: 0%

---

# Problemas após desabilitar um módulo

Este artigo fornece uma solução para problemas de funcionalidade do módulo após desativar a saída do módulo no Commerce Admin.

## Produtos e versões afetados

* Adobe Commerce na infraestrutura em nuvem 2.1.X ou anterior
* Adobe Commerce no local 2.1.X ou anterior

## Problema

Tendo desabilitado a saída do módulo no Administrador do Commerce, em **Lojas** > **Configurações** > **Configuração** > AVANÇADO > **Avançado**, você poderá começar a ver problemas relacionados à funcionalidade do módulo.

## Causa

Desabilitar uma saída de módulo em **Lojas** > **Configurações** > **Configuração** > AVANÇADO > **Avançado** desabilita somente a saída (HTML, JS), mas não desabilita a funcionalidade deste módulo.

## Solução

Se você precisar desabilitar a funcionalidade do módulo, desabilite o módulo conforme descrito em [Habilitar ou desabilitar módulos](https://devdocs.magento.com/guides/v2.1/install-gde/install/cli/install-cli-subcommands-enable.html) na documentação do desenvolvedor.

A funcionalidade de desabilitação de saída do módulo foi removida a partir da versão 2.2.0.
