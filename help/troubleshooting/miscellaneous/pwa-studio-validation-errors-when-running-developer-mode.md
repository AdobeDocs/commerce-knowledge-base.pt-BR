---
title: 'PWA Studio: erros de validação ao executar o modo de desenvolvedor'
description: Este tópico discute uma solução para quando ocorrem erros de validação ao executar o modo de desenvolvedor no Progressive Web App (PWA) Studio for Adobe Commerce como resultado de não ter criado anteriormente o conceito venia (Venia é uma loja da PWA). arquivo de ambiente. Esse arquivo manterá as variáveis para o ambiente de desenvolvimento local.
exl-id: 97d042ef-88e6-4eda-a834-2cff4de276e2
feature: Configuration
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 0%
---
# PWA Studio: erros de validação ao executar o modo de desenvolvedor

Este tópico discute uma solução para quando ocorrem erros de validação ao executar o modo de desenvolvedor no Progressive Web App (PWA) Studio for Adobe Commerce como resultado de não ter criado anteriormente o conceito venia (Venia é uma loja da PWA). arquivo de ambiente. Esse arquivo manterá as variáveis para o ambiente de desenvolvimento local.

## Produtos e versões afetados

* PWA Studio para Adobe Commerce

## Problema

<u>Etapa de reprodução</u>:

* Execute o modo de desenvolvedor no PWA Studio para Adobe Commerce.

<u>Resultado esperado</u>:

* O servidor do PWA Studio é iniciado normalmente.

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

* [Documentação do PWA Studio para Adobe Commerce](https://developer.adobe.com/commerce/pwa-studio/)
* [Loja Venia (Conceito)](https://developer.adobe.com/commerce/pwa-studio/guides/packages/venia/)
