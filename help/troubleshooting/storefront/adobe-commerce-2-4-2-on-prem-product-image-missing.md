---
title: "Adobe Commerce no local 2.4.2: imagem do produto ausente"
description: Este artigo descreve um problema conhecido do Adobe Commerce no local 2.4.2 em que a imagem do produto não é carregada na página do produto. Este problema está programado para ser resolvido em uma versão futura após a versão 2.4.3. Não há uma solução disponível no momento, mas, como solução alternativa, você pode desativar o Nginx para redimensionar imagens.
exl-id: c4d9240e-5df5-4eab-bb4e-1f06f9bd3a1e
feature: Iaas, Products, Storefront
role: Admin
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 0%

---

# Adobe Commerce no local 2.4.2: imagem do produto ausente

Este artigo descreve um problema conhecido do Adobe Commerce no local 2.4.2 em que a imagem do produto não é carregada na página do produto. Este problema está programado para ser resolvido em uma versão futura após a versão 2.4.3. Não há uma solução disponível no momento, mas, como solução alternativa, você pode desativar o Nginx para redimensionar imagens.

## Produtos e versões afetados

* Adobe Commerce no local 2.4.2

## Problema

A imagem do produto é salva na tag `s3` bucket, mas não é sincronizado de volta ao `pub/media` diretório. Esse problema ocorre somente ao usar:

* Nginx habilitado para o site para redimensionar imagens
* AWS `s3` como armazenamento de mídia

<u>Pré-requisitos</u>:

Adobe Commerce instalado com Nginx.

<u>Etapas a serem reproduzidas</u>:

1. Configurar o Adobe Commerce para usar o AWS `s3` como armazenamento de mídia.
1. Configure o Nginx usando o `nginx.conf.sample` arquivo de configuração fornecido no diretório de instalação do Adobe Commerce e um host virtual Nginx. Consulte [Configurar Nginx](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/nginx.html#configure-nginx-ubuntu) na documentação do desenvolvedor.
1. Crie um produto simples com uma imagem de produto.
1. O Nginx tem uma configuração sem comentários para redimensionamento da imagem no `nginx.conf.sample` semelhante a este:

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
