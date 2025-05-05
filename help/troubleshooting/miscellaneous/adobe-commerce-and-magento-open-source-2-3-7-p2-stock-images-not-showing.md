---
title: Imagens do Stock não exibidas, Adobe Commerce e Magento Open Source 2.3.7-p2
description: Este artigo fornece uma solução para o problema em que as imagens do Adobe stock carregadas nos diretórios do sistema de arquivos "pub/media" ou "pub/media/catalog" não são exibidas na interface do usuário da Galeria de mídia. Isso ocorre porque as imagens estão fora dos diretórios de galeria de mídia permitidos. Para que essas imagens exibam, os comerciantes precisam excluir as imagens no sistema de arquivos e fazer upload novamente em um diretório da Galeria de mídia permitido.
exl-id: 84488d87-095f-4739-858f-19a52d6e5822
feature: Categories, Orders
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '393'
ht-degree: 0%

---

# Imagens do Stock não exibidas, Adobe Commerce e Magento Open Source 2.3.7-p2

Este artigo fornece uma solução para o problema em que as imagens do Adobe carregadas nos diretórios do sistema de arquivos `pub/media` ou `pub/media/catalog` não são exibidas na interface do usuário da Galeria de Mídia. Isso ocorre porque as imagens estão fora dos diretórios de galeria de mídia permitidos. Para que essas imagens exibam, os comerciantes precisam excluir as imagens no sistema de arquivos e fazer upload novamente em um diretório da Galeria de mídia permitido.

## Produtos e versões afetados

* Adobe Commerce e Magento Open Source 2.3.7-p2


## Problema

Os comerciantes podem fazer upload de imagens do Adobe Stock para a Raiz de armazenamento na Galeria de mídia, mas essas imagens não aparecem na interface do usuário e aparecerão como se não tivessem sido carregadas. Isso ocorre porque o sistema observa que a imagem já foi carregada no sistema de arquivos, embora não esteja disponível na interface do Media Gallery. Isso significa que depois que um comerciante carrega uma imagem para `pub/media` ou `pub/media/catalog`, ele não pode usar essa imagem até que ela seja excluída diretamente no sistema de arquivos.

<u>Etapas a serem reproduzidas</u>

1. Ative o Adobe Stock com chaves de API válidas.
1. Abra a galeria de mídia (**Catálogo** > **Categorias** > seção **Conteúdo** > clique em **Selecionar da Galeria**).
1. Clique em **Pesquisar Adobe Stock**.
1. Selecione uma imagem. Clique em **Salvar visualização**. Observe que talvez seja necessário redefinir a grade do Adobe Stock para que as imagens sejam exibidas.

<u>Resultado esperado</u>:

A imagem é exibida.

<u>Resultado real</u>:

Uma mensagem de erro é exibida: *Não é possível localizar a imagem. Não é possível localizar esta imagem na galeria de mídia.*

## Causa

As imagens podem ser carregadas na Raiz de armazenamento da galeria de mídia por meio do Adobe Stock.

## Solução

Selecione qualquer subdiretório da Raiz de Armazenamento da Galeria de Mídia (excluindo **Raiz de Armazenamento** > **Catálogo**) antes de carregar uma imagem do Adobe Stock.
Exclua as imagens Adobe Stock carregadas das pastas `pub/media` e `pub/media/catalog` no sistema de arquivos do Adobe Commerce e carregue as imagens em quaisquer subdiretórios Raiz de Armazenamento da Galeria de Mídia permitidos (excluindo **Raiz de Armazenamento** > **Catálogo**).

## Leitura relacionada

* [Armazenamento de mídia](https://experienceleague.adobe.com/pt-br/docs/commerce-admin/content-design/wysiwyg/storage/media-storage) em nosso guia do usuário.
