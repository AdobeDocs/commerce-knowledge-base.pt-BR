---
title: Não é possível excluir a origem ou alterar seu código
description: Este artigo fornece uma correção para quando não é possível remover completamente uma fonte e/ou alterar seu código.
exl-id: dbdb4d62-9138-4a3d-a58f-8671f1dc5b42
feature: Console
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 0%

---

# Não é possível excluir a origem ou alterar seu código

Este artigo fornece uma correção para quando não é possível remover completamente uma fonte e/ou alterar seu código.

## Problema

As origens não podem ser excluídas independentemente da atribuição do produto.

## Produtos e versões afetados

* Adobe Commerce na infraestrutura em nuvem (todas as versões), com o Magento Inventory instalado
* Adobe Commerce no local 2.3.0 e posterior, com inventário de Magento instalado
* Magento Open Source 2.3.0 e mais recente, com inventário de Magento instalado

## Causa

Por design, não é possível remover completamente uma fonte e/ou alterar seu código.

A remoção de uma origem causaria problemas nos dados do pedido porque as origens fazem parte dos inventários de produtos, pedidos, dados de remessa e muito mais.

O código é essencial para conectar a origem aos pedidos. Este é um identificador exclusivo para a origem e está desativado para edição.

## Solução

Você pode remover uma origem de um produto transferindo o inventário ou descartando o produto de todas as remessas em um local.

Se você precisar remover uma origem dos cálculos de [SSA](https://devdocs.magento.com/guides/v2.3/inventory/source-selection-algorithms.html) e do processamento de ordem do Adobe Commerce Inventory, poderá desabilitar a origem. As fontes desativadas retêm todos os dados, os produtos atribuídos e as quantidades de inventário, e podem ser reativadas a qualquer momento para começar a entrega novamente.

Consulte o [guia Criar Fontes](https://github.com/magento/inventory/wiki/Create-Sources#disable-sources) para obter detalhes sobre como desabilitar uma origem.
