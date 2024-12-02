---
title: 'PWA Studio: Erros de validação ao executar o modo de desenvolvedor'
description: Este tópico discute uma solução para quando ocorrem erros de validação ao executar o modo de desenvolvedor no Estúdio de aplicativo web progressivo (PWA) para Adobe Commerce como resultado de não ter criado anteriormente o arquivo de ambiente venia-concept (Venia é uma loja de PWA). Esse arquivo manterá as variáveis para o ambiente de desenvolvimento local.
exl-id: 97d042ef-88e6-4eda-a834-2cff4de276e2
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 0%

---

# PWA Studio: Erros de validação ao executar o modo de desenvolvedor

Este tópico discute uma solução para quando ocorrem erros de validação ao executar o modo de desenvolvedor no Estúdio de aplicativo web progressivo (PWA) para Adobe Commerce como resultado de não ter criado anteriormente o arquivo de ambiente venia-concept (Venia é uma loja de PWA). Esse arquivo manterá as variáveis para o ambiente de desenvolvimento local.

## Produtos e versões afetados

* PWA Studio para Adobe Commerce

## Problema

<u>Etapa de reprodução</u>:

* Execute o modo de desenvolvedor no PWA Studio para Adobe Commerce.

<u>Resultado esperado</u>:

* O servidor PWA Studio é iniciado normalmente.

<u>Resultado real</u>:

* Você vê erros de validação, que podem ser semelhantes a:

```
    ⓧ  Missing required environment variables:         MAGENTO_BACKEND_URL: Connect to an instance of Adobe Commerce 2.3 by specifying its public domain name. (eg.         "https://master-7rqtwti-mfwmkrjfqvbjk.us-4.magentosite.cloud/")      ⚠  No .env file in ./packages/venia-concept. Autogenerate a .env file by running the command 'buildpack         create-env-file ./packages/venia-concept'.
```

## Causa

O arquivo de variáveis de ambiente para o ambiente de desenvolvimento local está ausente. O arquivo gerado pelo comando abaixo manterá as variáveis para o ambiente de desenvolvimento local.

## Solução

Execute o comando

```
npx @magento/pwa-buildpack create-env-file packages/venia-concept
```

no diretório raiz para gerar o arquivo que manterá as variáveis para o ambiente de desenvolvimento local.

## Leitura relacionada

* [PWA Studio para a documentação do Adobe Commerce](https://magento.github.io/pwa-studio/)
* [Loja Venia (Conceito)](https://magento.github.io/pwa-studio/venia-pwa-concept/)
