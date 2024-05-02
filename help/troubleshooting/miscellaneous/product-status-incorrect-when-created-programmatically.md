---
title: Status do produto incorreto quando criado programaticamente
description: Este artigo fornece uma correção para quando o status do produto é Desativado e os produtos não são exibidos na loja ou são atribuídos às visualizações incorretas da loja quando criados/atualizados programaticamente.
exl-id: ac02f961-f9e2-4620-839f-b8dbd0befb15
feature: Products
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
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

O problema pode aparecer devido a restrições de ACL definidas para as funções de administrador da instância do Adobe Commerce. No caso de um aplicativo inicializado, não haverá sessões de administrador inicializadas com configurações de ACL apropriadas. Isso causaria a falha das validações no `Magento_AdminGws` que é responsável pela verificação de permissões dessas ações.

## Solução para status de produto incorreto

Defina uma preferência de ID dinâmica para a variável `Magento\Framework\Authorization\PolicyInterface`, conforme descrito na seção [ObjectManager>Atualizações programáticas do produto](https://devdocs.magento.com/guides/v2.3/extension-dev-guide/object-manager.html#programmatic-product-updates) tópico na documentação do desenvolvedor.

## Leitura relacionada

* [GitHub: não é possível alterar o status do produto que foi criado com o productRepository](https://github.com/magento/magento2/issues/5664)
