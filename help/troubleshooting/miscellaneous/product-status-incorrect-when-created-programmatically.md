---
title: Status do produto incorreto quando criado programaticamente
description: Este artigo fornece uma correção para quando o status do produto é Desativado e os produtos não são exibidos na loja ou são atribuídos às visualizações incorretas da loja quando criados/atualizados programaticamente.
exl-id: ac02f961-f9e2-4620-839f-b8dbd0befb15
feature: Products
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '212'
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

* [Github: não é possível alterar o status do produto que foi criado com productRepository](https://github.com/magento/magento2/issues/5664)
