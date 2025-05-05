---
title: Site em modo de manutenção, mas disponível para clientes
description: Este artigo fornece uma correção para quando o modo de manutenção está ativado (um problema de Adobe Commerce na infraestrutura em nuvem), mas a loja ainda está disponível para os clientes.
exl-id: 61b81fbd-a382-44b5-94e9-5b6d72f11349
feature: Cache
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
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

[Habilite ou desabilite o modo de manutenção](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) na documentação do desenvolvedor.
