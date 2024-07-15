---
title: Cores lentas, lentas e de longa duração
description: Este artigo descreve como resolver problemas de desempenho do site e crons de execução e travamento lentos causados por tabelas simples e indexadores ativados.
exl-id: a78ca3c3-85b4-40a1-a693-4703dd3ef4b5
feature: Best Practices, Cache, Categories, Catalog Management
role: Developer
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 0%

---

# Cores lentas, lentas e de longa duração

>[!WARNING]
>
>Em qualquer versão do Adobe Commerce, como algumas extensões funcionam somente com tabelas simples, há um risco se você desativar as tabelas simples. Se você souber que tem algumas extensões que usam indexadores de Catálogo Simples, talvez precise levar isso em consideração ao definir esses valores como &quot; *Não* &quot;.

Este artigo descreve como resolver problemas de desempenho do site e cronogramas de execução lenta e travados causados por [tabelas simples e indexadores](https://docs.magento.com/m2/ce/user_guide/catalog/catalog-flat.html) habilitados.

PRODUTOS E VERSÕES AFETADOS

* Adobe Commerce na infraestrutura em nuvem 2.1.x e superior
* Adobe Commerce no local 2.1.x e superior
* Magento Open Source 2.1.x e superior

## Problema

Indexadores simples podem causar:

* Problemas de carregamento intenso de SQL e desempenho do site.
* Cordões de corrida longa e travados.

## Causa

Tabelas simples e indexadores habilitados.

## Solução {#solution}

A partir do Adobe Commerce e do Magento Open Source 2.1.x e superior, o uso de um catálogo simples não é mais uma prática recomendada e não é recomendado. O uso continuado desse recurso é conhecido por causar degradação de desempenho e outros problemas de indexação. Para desativar o catálogo simples:

1. No Administrador, navegue até **Lojas** > **Configurações** > **Configuração**.
1. No painel à esquerda, em **Catálogo**, escolha **Catálogo**.
1. Expanda a seção **Vitrine** e faça o seguinte:
   * Definir **Usar Categoria de Catálogo Simples** como *Não*.
   * Definir **Usar Produto de Catálogo Simples** como *Não*.
1. Quando terminar, clique em **Salvar configuração**. Em seguida, quando solicitado, atualize o cache.
1. Liberar cache executando `php bin/magento cache:flush`.

Se você não puder alterar a **Usar Categoria de Catálogo Simples** e o **Usar Produto de Catálogo Simples** para *Não* porque as opções estão esmaecidas, desabilite indexadores simples no `app/etc/config.php`:

1. Execute este comando para verificar se todos os indexadores estão definidos como Update by schedule: `php bin/magento indexer:set-mode schedule`.
1. Edite `app/etc/config.php` e localize as linhas com `flat_catalog_product` e `flat_catalog_category` - altere-as de 1 para 0 para desabilitá-las.
1. Executar o comando `php bin/magento app:config:import`
1. Execute este comando para confirmar se os indexadores simples estão desabilitados: `php        bin/magento indexer:status`.
1. Liberar cache executando `php bin/magento cache:flush`.

## Informações relacionadas

[Redefinir trabalhos cron do Adobe Commerce travados manualmente na Nuvem](/help/how-to/general/reset-stuck-magento-cron-jobs-manually-on-cloud.md) em nossa base de dados de conhecimento de suporte.
