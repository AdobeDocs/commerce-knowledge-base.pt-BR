---
title: 'PWA Studio: o Webpack trava antes de iniciar a compilação'
description: Este artigo fala sobre uma solução sugerida para quando um javascript [Webpack](https://developer.adobe.com/commerce/pwa-studio/guides/project/tools-libraries/#webpack) trava por um longo tempo antes de iniciar a compilação no Progressive Web App Studio (PWA Studio).
exl-id: 692eeafa-9289-4d66-9f2f-1e0fe36e681d
feature: Configuration
role: Developer
source-git-commit: 032fe4d32921c63570672b9c68e8c03e00bd1077
workflow-type: tm+mt
source-wordcount: '270'
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

* Se estiver usando o    ```yaml    build    ```    normalmente, ele gera os artefatos de build para o Venia.
* Se estiver usando o    ```yaml    watch    ```    inicia a loja Venia normalmente.

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

* [Webpack de Javascript: Conceitos](https://webpack.js.org/concepts/)
* [Configuração da vitrine Venia](https://developer.adobe.com/commerce/pwa-studio/guides/packages/venia/)
* [Pacote de compilação do PWA](https://developer.adobe.com/commerce/pwa-studio/guides/packages/buildpack/)
* [Interface de Linha de Comando do buildpack](https://developer.adobe.com/commerce/pwa-studio/api/buildpack/cli/)
* [Ferramentas e bibliotecas: buildpack](https://developer.adobe.com/commerce/pwa-studio/guides/project/tools-libraries/#webpack)
