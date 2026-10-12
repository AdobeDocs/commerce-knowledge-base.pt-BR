---
title: 'PWA Studio: o Webpack trava antes de iniciar a compilação'
description: Este artigo fala sobre uma solução sugerida para quando um javascript [Webpack](https://developer.adobe.com/commerce/pwa-studio/guides/project/tools-libraries/#webpack) trava por um longo tempo antes de iniciar a compilação no Progressive Web App Studio (PWA Studio).
exl-id: 692eeafa-9289-4d66-9f2f-1e0fe36e681d
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
source-wordcount: '332'
ht-degree: 0%
---
# PWA Studio: o Webpack trava antes de iniciar a compilação

Este artigo fala sobre uma solução sugerida para quando um javascript [Webpack](https://developer.adobe.com/commerce/pwa-studio/guides/project/tools-libraries/#webpack) trava por muito tempo antes de iniciar a compilação no Progressive Web App Studio (PWA Studio).

## Produtos e versões afetados

* PWA Studio

## Problema

[Verifique qual é a versão mais recente do pwa-buildpack](https://github.com/magento/pwa-studio/tree/master/packages/pwa-buildpack) e a

```yaml
pwa-buildpack
```

o número da versão estará ao lado da lista de nomes de arquivo `package.json`. Se você tiver uma versão antiga do

```yaml
pwa-buildpack
```

projeto, o webpack pode travar por muito tempo antes de iniciar a compilação.

<u>Etapas a serem reproduzidas</u>:

<u>Pré-requisitos</u>: configure uma loja da PWA Studio, como Venia, com uma instância do Adobe Commerce local e execute um

```yaml
build
```

ou

```yaml
watch
```

comando.

<u>Resultado esperado</u>:

* Se estiver usando o comando `build`, ele gera os artefatos de compilação para Venia normalmente.
* Se estiver usando o comando `watch`, ele iniciará a loja Venia normalmente.

<u>Resultado real</u>:

Seu

```yaml
build
```

ou

```yaml
watch
```

parece estar paralisado e não será concluído, nem serão exibidos erros.

## Soluções

Atualize o projeto usando o seguinte comando:

```yaml
yarn upgrade
```

Verifique se você tem uma versão atual do openssl em seu sistema usando o seguinte comando:

```yaml
openssl version
```

A versão deve ser a 1.0 ou superior (ou LibreSSL 2, no caso do OSX High Sierra).

Você pode instalar versões superiores do OpenSSL com o [Homebrew](https://brew.sh/) no OSX, o [Chocolatey](https://chocolatey.org/) no Windows ou o gerenciador de pacotes da sua distribuição Linux.

## Leitura relacionada

* [Javascript Webpack: Conceitos](https://webpack.js.org/concepts/)
* [Configuração da vitrine Venia](https://developer.adobe.com/commerce/pwa-studio/guides/packages/venia/)
* [PWA Builder Pack](https://developer.adobe.com/commerce/pwa-studio/guides/packages/buildpack/)
* [Interface de linha de comando do buildpack](https://developer.adobe.com/commerce/pwa-studio/api/buildpack/cli/)
* [Ferramentas e bibliotecas: buildpack](https://developer.adobe.com/commerce/pwa-studio/guides/project/tools-libraries/#webpack)

