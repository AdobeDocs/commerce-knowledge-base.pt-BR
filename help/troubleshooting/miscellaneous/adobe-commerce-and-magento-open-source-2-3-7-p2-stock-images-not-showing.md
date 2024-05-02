---
title: Imagens do Stock não exibidas, Adobe Commerce e Magento Open Source 2.3.7-p2
description: Este artigo fornece uma solução para o problema em que as imagens do Adobe stock carregadas nos diretórios do sistema de arquivos "pub/media" ou "pub/media/catalog" não são exibidas na interface do usuário da Galeria de mídia. Isso ocorre porque as imagens estão fora dos diretórios de galeria de mídia permitidos. Para que essas imagens exibam, os comerciantes precisam excluir as imagens no sistema de arquivos e fazer upload novamente em um diretório da Galeria de mídia permitido.
exl-id: 84488d87-095f-4739-858f-19a52d6e5822
feature: Categories, Orders
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '393'
ht-degree: 0%

---

# Imagens do Stock não exibidas, Adobe Commerce e Magento Open Source 2.3.7-p2

Este artigo fornece uma solução para o problema em que as imagens do Adobe são carregadas nos diretórios do sistema de arquivos `pub/media` ou `pub/media/catalog` não são exibidos na interface da Galeria de mídia. Isso ocorre porque as imagens estão fora dos diretórios de galeria de mídia permitidos. Para que essas imagens exibam, os comerciantes precisam excluir as imagens no sistema de arquivos e fazer upload novamente em um diretório da Galeria de mídia permitido.

## Produtos e versões afetados

* Adobe Commerce e Magento Open Source 2.3.7-p2


## Problema

Os comerciantes podem fazer upload de imagens do Adobe Stock para a Raiz de armazenamento na Galeria de mídia, mas essas imagens não aparecem na interface do usuário e aparecerão como se não tivessem sido carregadas. Isso ocorre porque o sistema observa que a imagem já foi carregada no sistema de arquivos, embora não esteja disponível na interface do Media Gallery. Isso significa que quando um comerciante carregar uma imagem para `pub/media` ou `pub/media/catalog`, eles não poderão usar essa imagem até que ela seja excluída diretamente no sistema de arquivos.

<u>Etapas a serem reproduzidas</u>

1. Ative o Adobe Stock com chaves de API válidas.
1. Abrir galeria de mídia (**Catálogo** > **Categorias** > **Conteúdo** seção > clique **Selecionar na Galeria**).
1. Clique em **Pesquisar no Adobe Stock**.
1. Selecione uma imagem. O botão **Salvar visualização**. Observe que talvez seja necessário redefinir a grade do Adobe Stock para que as imagens sejam exibidas.

<u>Resultado esperado</u>:

A imagem é exibida.

<u>Resultado real</u>:

Uma mensagem de erro é exibida: *Não é possível localizar a imagem. Não é possível encontrar esta imagem na galeria de mídia.*

## Causa

As imagens podem ser carregadas na Raiz de armazenamento da galeria de mídia por meio do Adobe Stock.

## Solução

Selecione qualquer subdiretório da Raiz de armazenamento da galeria de mídia (excluindo **Raiz de armazenamento** > **Catálogo**) antes de carregar uma imagem Adobe Stock.
Exclua as imagens carregadas do Adobe Stock da `pub/media` e `pub/media/catalog` pastas no sistema de arquivos do Adobe Commerce e fazer upload de imagens em qualquer subdiretório raiz de armazenamento do Media Gallery permitido (excluindo **Raiz de armazenamento** > **Catálogo**).

## Leitura relacionada

* [Armazenamento de mídia](https://docs.magento.com/user-guide/v2.3/cms/media-storage.html) em nosso guia do usuário.
