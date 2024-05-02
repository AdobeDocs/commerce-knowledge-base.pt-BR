---
title: "Adobe Commerce 2.4.1: página vazia quando o formulário dotdigital Page Builder é salvo"
description: Este artigo fornece uma solução alternativa para um problema conhecido no Adobe Commerce 2.4.1 para mostrar uma página da Web vazia após salvar um formulário dotdigital do Page Builder no Painel de administração ao usar o navegador Safari.
exl-id: 682eac73-1ad2-4093-acfb-6a8da4c05cf5
feature: Page Builder
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '249'
ht-degree: 0%

---

# Adobe Commerce 2.4.1: página vazia quando o formulário dotdigital Page Builder é salvo

Este artigo fornece uma solução alternativa para um problema conhecido no Adobe Commerce 2.4.1 para mostrar uma página da Web vazia após salvar um formulário dotdigital do Page Builder no Painel de administração ao usar o navegador Safari.

## Produtos e versões afetados

* Adobe Commerce no local 2.4.1
* Adobe Commerce na infraestrutura em nuvem 2.4.1

## Problema

<u>Etapas a serem reproduzidas</u>

1. Ir para **Painel de administração** > **Conteúdo** > **Páginas** e selecione **Editar** de qualquer página.
1. Ir para **Conteúdo** e clique no link **Editar com o Page Builder** botão.
1. Arraste o **dotdigital form** bloquear e selecionar **Editar**.
1. Selecione um dos formulários de teste e escolha **Incorporado** e salve o formulário.
1. Salve a modificação da página.

<u>Resultado esperado:</u>

A página da Web deve ser salva com sucesso.

<u>Resultado real:</u>

A página da Web está vazia. Depois de recarregar a página da Web, as alterações são aplicadas.

## Solução alternativa

A solução alternativa é usar um navegador alternativo para o Safari. O problema está programado para ser corrigido na próxima versão, Adobe Commerce 2.4.2, no primeiro trimestre de 2021.

## Leitura relacionada

* [O que é o Page Builder?](https://devdocs.magento.com/page-builder/docs/) na documentação do desenvolvedor.
* [Configuração do Page Builder](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/setup.html) na documentação do desenvolvedor.
* [Page Builder](https://docs.magento.com/user-guide/cms/page-builder.html) em nosso guia do usuário.
* [Page Builder - Elementos](https://docs.magento.com/user-guide/cms/page-builder-elements.html) em nosso guia do usuário.
