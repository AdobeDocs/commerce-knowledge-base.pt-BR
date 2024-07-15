---
title: Site em modo de manutenção, mas disponível para clientes
description: Este artigo fornece uma correção para quando o modo de manutenção está ativado (um problema de Adobe Commerce na infraestrutura em nuvem), mas a loja ainda está disponível para os clientes.
exl-id: 61b81fbd-a382-44b5-94e9-5b6d72f11349
feature: Cache
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '149'
ht-degree: 0%

---

# Site em modo de manutenção, mas disponível para clientes

Este artigo fornece uma correção para quando o modo de manutenção está ativado (um problema de Adobe Commerce na infraestrutura em nuvem), mas a loja ainda está disponível para os clientes.

## Produtos e versões afetados

* Adobe Commerce na infraestrutura em nuvem (todas as versões)

## Problema

<u>Etapas a serem reproduzidas:</u>

1. Habilite o modo de manutenção para o site.
1. Navegue até a loja.

<u>Resultado esperado:</u>

A página de manutenção é exibida.

<u>Resultado real:</u>

As páginas de vitrine são exibidas como de costume.

## Causa

As páginas ainda são armazenadas em cache, portanto, a página de manutenção não é exibida.

## Solução para o site visível apesar de estar no modo de manutenção

1. SSH para o seu ambiente.
1. Execute o comando `php bin/magento cache:clean`.

## Leitura relacionada

[Habilite ou desabilite o modo de manutenção](https://devdocs.magento.com/guides/v2.3/install-gde/install/cli/install-cli-subcommands-maint.html) na documentação do desenvolvedor.
