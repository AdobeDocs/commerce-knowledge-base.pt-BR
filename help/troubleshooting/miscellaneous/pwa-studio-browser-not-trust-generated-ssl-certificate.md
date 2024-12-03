---
title: 'PWA Studio: o navegador não confia no certificado SSL gerado'
description: Este artigo fornece uma solução para um aviso de certificado SSL gerado não confiável em seu navegador quando você navega para uma instância local de sua loja de PWA Studio durante o desenvolvimento.
exl-id: b7bfe1e6-5832-4472-9e51-f04b8583428a
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 0%

---

# PWA Studio: o navegador não confia no certificado SSL gerado

Este artigo fornece uma solução para um aviso de certificado SSL gerado não confiável em seu navegador quando você navega para uma instância local de sua loja de PWA Studio durante o desenvolvimento.

## Produtos e versões afetados

PWA Studio para Adobe Commerce

## Problema

O navegador não confia no certificado SSL gerado pela loja de PWA Studio local.

## Causa

Navegar até o site de desenvolvimento/preparo.

## Solução

No projeto da loja, execute o comando para adicionar um nome de host personalizado e um certificado SSL à instância de desenvolvimento local:

```sh
yarn buildpack create-custom-origin ./
```

A geração de certificados é realizada por [devcert](https://github.com/davewasmer/devcert). Depende do OpenSSL, portanto, verifique se você tem uma versão atual do openssl no seu sistema usando o seguinte comando:

`openssl version`

A versão deve ser a 1.0 ou superior (ou LibreSSL 2, no caso do OSX High Sierra).

Você pode instalar versões superiores do OpenSSL com o [Homebrew](https://brew.sh/) no OSX, o [Chocolatey](https://chocolatey.org/) no Windows ou o gerenciador de pacotes da sua distribuição Linux.

Se você estiver executando o Linux, verifique se o `libnss3-tools` (ou o equivalente) está instalado em seu sistema. Mais informações fornecidas nesta seção do arquivo readme [devcert](https://github.com/davewasmer/devcert#skipcertutil).

Alguns usuários sugeriram excluir a pasta devcert para acionar a regeneração do certificado.

* Para usuários do MacOS, esta pasta geralmente é encontrada em: `{{~/Library/Application Support/devcert }}`
* Para usuários do Windows, esta pasta geralmente é encontrada em: `${User}\AppData\Local\devcert`

## Leitura relacionada em nossa base de conhecimento de suporte

* [PWA Studio: Erro de confiança de certificado autoassinado](https://support.magento.com/hc/en-us/articles/360038973172)
* [PWA Studio: o Webpack trava antes de iniciar a compilação](/help/troubleshooting/miscellaneous/pwa-studio-webpack-hangs-before-beginning-compilation.md)
* [PWA Studio: O navegador exibe o erro &quot;Não é possível usar proxy para&quot;](/help/troubleshooting/miscellaneous/pwa-studio-browser-displays-cannot-proxy-to-error.md)
* [PWA Studio: Erros de validação ao executar o modo de desenvolvedor](/help/troubleshooting/miscellaneous/pwa-studio-validation-errors-when-running-developer-mode.md)
