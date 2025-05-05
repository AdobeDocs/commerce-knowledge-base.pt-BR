---
title: 'Adobe Commerce no local 2.4.2: imagem do produto ausente'
description: Este artigo descreve um problema conhecido do Adobe Commerce no local 2.4.2 em que a imagem do produto não é carregada na página do produto. Este problema está programado para ser resolvido em uma versão futura após a versão 2.4.3. Não há uma solução disponível no momento, mas, como solução alternativa, você pode desativar o Nginx para redimensionar imagens.
exl-id: c4d9240e-5df5-4eab-bb4e-1f06f9bd3a1e
feature: Iaas, Products, Storefront
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 0%

---

# Adobe Commerce no local 2.4.2: imagem do produto ausente

Este artigo descreve um problema conhecido do Adobe Commerce no local 2.4.2 em que a imagem do produto não é carregada na página do produto. Este problema está programado para ser resolvido em uma versão futura após a versão 2.4.3. Não há uma solução disponível no momento, mas, como solução alternativa, você pode desativar o Nginx para redimensionar imagens.

## Produtos e versões afetados

* Adobe Commerce no local 2.4.2

## Problema

A imagem do produto é salva no bucket `s3`, mas não é sincronizada de volta ao diretório `pub/media`. Esse problema ocorre somente ao usar:

* Nginx habilitado para o site para redimensionar imagens
* AWS `s3` como armazenamento de mídia

<u>Pré-requisitos</u>:

Adobe Commerce instalado com Nginx.

<u>Etapas a serem reproduzidas</u>:

1. Configure o Adobe Commerce para usar o AWS `s3` como armazenamento de mídia.
1. Configure o Nginx usando o arquivo de configuração `nginx.conf.sample` fornecido no diretório de instalação do Adobe Commerce e um host virtual Nginx. Consulte [Configurar Nginx](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/installation-guide/prerequisites/web-server/nginx) na documentação do desenvolvedor.
1. Crie um produto simples com uma imagem de produto.
1. O Nginx tem uma configuração não comentada para redimensionamento de imagem em `nginx.conf.sample` semelhante a esta:

```conf
load_module /etc/nginx/modules/ngx_http_image_filter_module.so;
location /media/ {
    location ~* ^/media/catalog/.* {
        set $width "-";
        set $height "-";
        if ($arg_width != '') {
            set $width $arg_width;
        }
        if ($arg_height != '') {
            set $height $arg_height;
        }
        image_filter resize $width $height;
        image_filter_jpeg_quality 90;
    }
```

<u>Resultados esperados</u>:

A imagem do produto é carregada na página do produto.

<u>Resultados reais</u>:

A imagem do produto não é carregada na página do produto.

## Solução alternativa

Desative o Nginx para redimensionar imagens.
