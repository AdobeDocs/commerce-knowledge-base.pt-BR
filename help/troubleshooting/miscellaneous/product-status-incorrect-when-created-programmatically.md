---
title: Status do produto incorreto quando criado programaticamente
description: Este artigo fornece uma correção para quando o status do produto é Desativado e os produtos não são exibidos na loja ou são atribuídos às visualizações incorretas da loja quando criados/atualizados programaticamente.
exl-id: ac02f961-f9e2-4620-839f-b8dbd0befb15
feature: Products
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '227'
ht-degree: 0%
---
# Status do produto incorreto quando criado programaticamente

Este artigo fornece uma correção para quando o status do produto é Desativado e os produtos não são exibidos na loja ou são atribuídos às visualizações incorretas da loja quando criados/atualizados programaticamente.

## Produtos e versões afetados

* Adobe Commerce na infraestrutura em nuvem 2.X.X
* Adobe Commerce no local 2.X.X

## Problema

Quando os produtos de catálogo são criados ou atualizados programaticamente a partir de um script com o aplicativo Adobe Commerce inicializado, os produtos podem ter o status Desativado e/ou ser atribuídos às visualizações de loja erradas.

## Causa

O problema pode aparecer devido a restrições de ACL definidas para as funções de administrador da instância do Adobe Commerce. No caso de um aplicativo inicializado, não haverá sessões de administrador inicializadas com configurações de ACL apropriadas. Isso resultaria em falha nas validações no módulo `Magento_AdminGws`, que é responsável pela verificação de permissões dessas ações.

## Solução para status de produto incorreto

Defina uma preferência de ID dinâmica para o `Magento\Framework\Authorization\PolicyInterface`, conforme descrito no tópico [ObjectManager>Atualizações programáticas do produto](https://developer.adobe.com/commerce/php/development/components/object-manager/) da documentação do desenvolvedor.

## Leitura relacionada

* [GitHub: não é possível alterar o status do produto que foi criado com o productRepository](https://github.com/magento/magento2/issues/5664)
