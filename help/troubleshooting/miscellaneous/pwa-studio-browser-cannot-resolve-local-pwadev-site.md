---
title: "PWA Studio: o navegador não pode resolver o site .local.pwadev"
description: Este artigo fornece uma solução para quando outro programa ou processo editou seu [arquivo host](https://en.wikipedia.org/wiki/Hosts_(file\) e removeu a entrada do domínio do projeto.
exl-id: a1606016-906a-433f-9e40-9faa5f9bd790
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 0%

---

# PWA Studio: o navegador não pode resolver o site .local.pwadev

Este artigo fornece uma solução para quando outro programa ou processo tiver editado seu [arquivo host](https://en.wikipedia.org/wiki/Hosts_(file\)) e removido a entrada do domínio do projeto.

## Produtos e versões afetados

PWA Studio para Adobe Commerce

## Problema

Ao navegar para o site dev/de preparo, você não pode ver o site `.local.pwadev`.

## Causa

O PWA Studio permite atribuir um nome de host personalizado e um certificado SSL para o projeto ao computador local. Isso envolve a criação de uma nova entrada no arquivo de host do seu computador que se parece com algo como `my-storefront-project-abc123.local.pwadev`.

Essa entrada instrui qualquer navegador no computador do desenvolvedor a examinar o projeto da loja local quando ele acessar esse URL. Se outro programa ou processo entrar e remover essa entrada, o navegador não saberá para onde ir e o navegador não poderá resolver o site `.local.pwadev`.

## Solução

Você pode [editar manualmente seu arquivo de host](https://support.rackspace.com/how-to/modify-your-hosts-file/) para adicionar a entrada de volta, mas deve examinar seu outro software instalado para ver o que substituiu a alteração anterior.

## Leitura relacionada em nossa base de conhecimento de suporte

* [PWA Studio: Erro de confiança de certificado autoassinado](https://support.magento.com/hc/en-us/articles/360038973172)
* [PWA Studio: o Webpack trava antes de iniciar a compilação](/help/troubleshooting/miscellaneous/pwa-studio-webpack-hangs-before-beginning-compilation.md)
* [PWA Studio: O navegador exibe o erro &quot;Não é possível usar proxy para&quot;](/help/troubleshooting/miscellaneous/pwa-studio-browser-displays-cannot-proxy-to-error.md)
* [PWA Studio: Erros de validação ao executar o modo de desenvolvedor](/help/troubleshooting/miscellaneous/pwa-studio-validation-errors-when-running-developer-mode.md)
