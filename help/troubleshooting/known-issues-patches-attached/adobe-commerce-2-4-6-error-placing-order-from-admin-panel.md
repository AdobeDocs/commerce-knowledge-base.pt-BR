---
title: Ordem de inserção de erros do Adobe Commerce 2.4.6 no painel Admin
description: Este artigo fornece um patch para o problema conhecido do Adobe Commerce na infraestrutura em nuvem 2.4.6 quando você fica preso na seleção da loja depois de fazer um pedido no painel de administração do Commerce.
feature: Admin Workspace
role: Developer
exl-id: b30be5a5-3681-41db-9040-3624faed7c46
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 0%

---

# Ordem de inserção de erros do Adobe Commerce 2.4.6 no painel Admin

Este artigo fornece um patch para o problema conhecido do Adobe Commerce na infraestrutura em nuvem 2.4.6 quando você fica preso na seleção da loja depois de fazer um pedido no painel de administração do Commerce.

## Problema

Ao fazer um pedido pelo painel Admin, você fica preso na seleção da loja.

<u>Etapas a serem reproduzidas</u>

1. Ir para **[!UICONTROL Sales]** > **[!UICONTROL Orders]** e selecione um cliente para criar um pedido.
2. Selecione a loja para colocar o pedido na tela do seletor de loja.

<u>Resultado esperado</u>

Depois de selecionar a loja, você pode concluir o pedido.

<u>Resultado real:</u>

Depois de selecionar a loja, você é redirecionado de volta para a página do seletor de loja e não pode criar uma ordem.

## Correção

Clique no link a seguir para baixar o patch.

[Baixe o ACSD-52277_2.4.6.patch](assets/ACSD-52277_2.4.6.patch.zip)

### Versões compatíveis do Adobe Commerce

O patch foi criado para e compatível com o Adobe Commerce na infraestrutura em nuvem e Adobe Commerce no local 2.4.6 e 2.4.6-p1.

## Como aplicar o patch

* Para obter instruções sobre como aplicar patches para o Adobe Commerce na infraestrutura em nuvem, consulte [Aplicar patches](/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) em nosso Guia de infraestrutura do Commerce na nuvem.
* Para obter instruções sobre como aplicar patches para o Adobe Commerce no local, consulte [Aplicar patches](/docs/commerce-operations/upgrade-guide/patches/apply.html?lang=en#composer) em nosso Guia de atualização do Commerce.
