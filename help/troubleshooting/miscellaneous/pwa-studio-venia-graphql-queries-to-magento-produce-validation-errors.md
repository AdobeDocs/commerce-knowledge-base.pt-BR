---
title: "PWA Studio: as consultas do Venia GraphQL ao Adobe Commerce produzem erros de validação"
description: Este artigo fornece recomendações sobre como resolver o problema em que as consultas do GraphQL da loja Venia à instância do Adobe Commerce produzem erros de validação.
exl-id: ba268945-2a10-4af5-8089-cde21f0687bd
feature: GraphQL
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 0%

---

# PWA Studio: Consultas do Venia GraphQL ao Adobe Commerce geram erros de validação

Este artigo fornece recomendações sobre como resolver o problema em que as consultas do GraphQL da loja Venia à instância do Adobe Commerce produzem erros de validação.

## Produtos e versões afetados

* Adobe Commerce no local 2.2.x, 2.3.x
* Adobe Commerce na infraestrutura em nuvem 2.2.x, 2.3.x
* Projeto PWA Studio para Adobe Commerce

## Problema

As consultas do Venia GraphQL ao Adobe Commerce no local ou à Adobe Commerce na infraestrutura em nuvem produzem erros de validação.

## Causa

Um dos motivos que causam o problema pode ser o descompasso entre as consultas do Venia e do GraphQL e o esquema da instância conectada do Adobe Commerce.

## Solução

Para testar se as consultas estão atualizadas, execute o seguinte comando na raiz do projeto:

```bash
yarn run validate-queries
```

Isso mostrará um relatório de compatibilidade. Se você tiver incompatibilidades, precisará atualizar a instância do PWA Studio ou Adobe Commerce. Verifique a [Matriz de compatibilidade do Adobe Commerce](https://developer.adobe.com/commerce/pwa-studio/integrations/adobe-commerce/version-compatibility/) para ver exatamente as versões necessárias.

Consulte a documentação a seguir para obter instruções sobre como atualizar:

* Para atualizações de PWA Studio, procure a seção &quot;Atualização de uma versão anterior&quot; do [Notas de versão do PWA](https://github.com/magento/pwa-studio/releases/) para a versão para a qual você precisa atualizar.
* [Atualizar a versão do Adobe Commerce na infraestrutura em nuvem](https://devdocs.magento.com/cloud/project/project-upgrade.html) na documentação do desenvolvedor
* [Atualizar o Adobe Commerce no local (instalado usando &quot;criação de projeto do compositor&quot; ou arquivamento)](https://devdocs.magento.com/guides/v2.3/comp-mgr/cli/cli-upgrade.html) na documentação do desenvolvedor
* [Atualizar o Adobe Commerce no local (instalado pela clonagem do Adobe Commerce repo)](https://devdocs.magento.com/guides/v2.3/install-gde/install/cli/dev_update-magento.html) na documentação do desenvolvedor

## Leitura relacionada

* [PWA Studio: o Webpack trava antes de iniciar a compilação](/help/troubleshooting/miscellaneous/pwa-studio-webpack-hangs-before-beginning-compilation.md) em nossa base de conhecimento de suporte
* [PWA Studio: Erros de validação ao executar o modo de desenvolvedor](/help/troubleshooting/miscellaneous/pwa-studio-validation-errors-when-running-developer-mode.md) em nossa base de conhecimento de suporte
* [PWA Studio: O navegador exibe o erro &quot;Não é possível usar proxy para&quot;](/help/troubleshooting/miscellaneous/pwa-studio-browser-displays-cannot-proxy-to-error.md) em nossa base de conhecimento de suporte
* [Configurar NPM para poder usar o PWA Studio](/help/how-to/general/configure-npm-to-be-able-to-use-pwa-studio.md) em nossa base de conhecimento de suporte
* [PWA para a documentação do Adobe Commerce](https://magento.github.io/pwa-studio/)
