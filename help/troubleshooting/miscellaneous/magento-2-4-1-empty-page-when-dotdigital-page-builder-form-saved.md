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

1. Vá para **Painel de Administração** > **Conteúdo** > **Páginas** e selecione **Editar** de qualquer página.
1. Vá para **Conteúdo** e clique no botão **Editar com o Page Builder**.
1. Arraste o bloco **dotdigital form** e selecione **Editar**.
1. Selecione um dos formulários de teste, escolha o modo **Incorporado** e salve o formulário.
1. Salve a modificação da página.

<u>Resultado esperado:</u>

A página da Web deve ser salva com sucesso.

<u>Resultado real:</u>

A página da Web está vazia. Depois de recarregar a página da Web, as alterações são aplicadas.

## Solução alternativa

A solução alternativa é usar um navegador alternativo para o Safari. O problema está programado para ser corrigido na próxima versão, Adobe Commerce 2.4.2, no primeiro trimestre de 2021.

## Leitura relacionada

* [O que é o Page Builder?](https://devdocs.magento.com/page-builder/docs/) na documentação do desenvolvedor.
* [Configuração do Page Builder](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/setup.html) em nossa documentação do desenvolvedor.
* [Page Builder](https://docs.magento.com/user-guide/cms/page-builder.html) em nosso guia do usuário.
* [Page Builder - Elementos](https://docs.magento.com/user-guide/cms/page-builder-elements.html) no nosso guia do usuário.
