---
title: Erro de lista de desejos durante a atualização para o Adobe Commerce versões 2.3.4-p1 ou 2.3.5
description: Este artigo fornece uma correção para o problema conhecido ao atualizar para as versões 2.3.4-p1 e 2.3.5 do Adobe Commerce relacionadas a um erro de lista de desejos durante a atualização para essas versões.
exl-id: 97479615-bf3f-4544-a9c1-8f19ba74318e
feature: Install, Upgrade
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 6388cf7b-8a81-5248-a1e4-7bb57bbe250f
    internal-label: Install
  - id: a8ae7a5a-6cdc-5922-bd0d-6feb44b04984
    internal-label: Upgrade
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%
---
# Erro de lista de desejos durante a atualização para o Adobe Commerce versões 2.3.4-p1 ou 2.3.5

Este artigo fornece uma correção para o problema conhecido ao atualizar para as versões 2.3.4-p1 e 2.3.5 do Adobe Commerce relacionadas a um erro de lista de desejos durante a atualização para essas versões.

## Produtos e versões afetados

* Adobe Commerce na infraestrutura em nuvem 2.3.4-p1 e 2.3.5
* Adobe Commerce no local 2.3.4-p1 e 2.3.5

## Problema

Ao atualizar sua Adobe Commerce (todos os métodos de implantação) e o Magento Open Source para a versão 2.3.5 ou 2.3.4-p1, você pode obter um erro de lista de desejos (detalhado abaixo) do módulo:

```php
Magento_Wishlist
```

A atualização do Adobe Commerce (todos os métodos de implantação)/Magneto Open Source versão 2.3.4-p1 **para a versão 2.3.4-p2** ou do Adobe Commerce (todos os métodos de implantação)/Magneto Open Source versão 2.3.5 **para a versão 2.3.5-p1** corrigirá o erro.

<u>Etapas a serem reproduzidas</u>:

Atualize seu Adobe Commerce (todos os métodos de implantação)/Magento Open Source para a versão 2.3.4-p1 ou 2.3.5.

<u>Resultado esperado</u>:

O processo de atualização para o Adobe Commerce (todos os métodos de implantação)/Magento Open Source versão 2.3.4-p1 ou 2.3.5 é concluído normalmente.

<u>Resultado real</u>:

Durante a atualização, você recebe este erro:

```php
Module ‘Magento_Wishlist’:

Unable to apply data patch Magento\Wishlist\Setup\Patch\Data\CleanUpData for module Magento_Wishlist. Original exception message: Unable to unserialize value. Error: Syntax error
```

## Soluções

* Se você estava atualizando para Adobe Commerce (todos os métodos de implantação)/Magneto Open Source versão 2.3.5, **atualize para a versão 2.3.5-p1**. Adobe Commerce (todos os métodos de implantação)/Magento Open Source versão 2.3.5-p1 substitui 2.3.5.
* Se você estava atualizando para Adobe Commerce (todos os métodos de implantação)/Magento Open Source versão 2.3.4-p1, **atualize para a versão 2.3.4-p2**. Adobe Commerce (todos os métodos de implantação)/Magneto Open Source versão 2.3.4-p2 substitui a versão 2.3.4-p1.

## Leitura relacionada

Em nossa documentação do desenvolvedor:

* [guia da infraestrutura do Adobe Commerce na nuvem](https://experienceleague.adobe.com/pt-br/docs/commerce-cloud-service/user-guide/overview)
* [Adobe Commerce na infraestrutura em nuvem — atualização da versão do Adobe Commerce](https://experienceleague.adobe.com/pt-br/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version)
* [Adobe Commerce no local e Magento Open Source - atualize o aplicativo e os módulos do Adobe Commerce](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/upgrade-guide/overview)
* [Página de configuração do item da lista de desejos](https://developer.adobe.com/commerce/frontend-core/guide/layouts/product-layouts#wishlist-item-configure-page)
* [Módulos que fornecem relatórios avançados](https://developer.adobe.com/commerce/php/development/advanced-reporting/modules/)
