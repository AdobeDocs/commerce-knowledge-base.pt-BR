---
title: Status do estoque incorreto após a instalação do Inventory management
description: Este artigo fornece uma correção para o status do estoque que está incorreto após a instalação/atualização do Inventory management.
exl-id: ae32fbe3-deab-4f31-b427-95f8b54a476f
feature: Install, Inventory, Orders
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '194'
ht-degree: 0%

---

# Status do estoque incorreto após a instalação do Inventory management

Este artigo fornece uma correção para o status do estoque que está incorreto após a instalação/atualização do Inventory management.

## Status do estoque incorreto em alguns sites

Depois da primeira instalação ou atualização para ter o Inventory management no ambiente Adobe Commerce de vários sites, nem todos os sites têm os status de estoque corretos para os produtos.

## Produtos e versões afetados

* Adobe Commerce na infraestrutura em nuvem, todas as versões, com o Inventory management instalado
* Adobe Commerce no local 2.3.0 e posterior, com Inventory management instalado
* Magento Open Source 2.3.0 e mais recente, com Inventory management instalado

## Causa

Quando você instala/atualiza pela primeira vez, todos os seus produtos são atribuídos à origem padrão, associando todas as quantidades a essa origem. O Source padrão é atribuído ao Estoque padrão, com o Site padrão associado.

## Solução

Se você tiver mais de um site, precisará adicioná-los como Sales Channel no Estoque padrão ou em outros estoques personalizados.

Consulte a seção [Stock do wiki/guia do usuário](https://experienceleague.adobe.com/pt-br/docs/commerce-admin/inventory/stocks/stocks-manage) em nosso guia do usuário para obter detalhes sobre como fazer isso.
