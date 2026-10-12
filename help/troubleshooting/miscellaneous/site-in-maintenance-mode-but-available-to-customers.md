---
title: Site em modo de manutenção, mas disponível para clientes
description: Este artigo fornece uma correção para quando o modo de manutenção está ativado (um problema de Adobe Commerce na infraestrutura em nuvem), mas a loja ainda está disponível para os clientes.
exl-id: 61b81fbd-a382-44b5-94e9-5b6d72f11349
feature: Cache
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '159'
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

[Habilite ou desabilite o modo de manutenção](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) na documentação do desenvolvedor.
