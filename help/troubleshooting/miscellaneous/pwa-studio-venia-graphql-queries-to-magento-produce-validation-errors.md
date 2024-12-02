---
title: 'PWA Studio: Consultas do Venia GraphQL ao Adobe Commerce geram erros de validação'
description: Este artigo fornece recomendações sobre como resolver o problema em que as consultas do GraphQL da loja Venia à instância do Adobe Commerce produzem erros de validação.
exl-id: ba268945-2a10-4af5-8089-cde21f0687bd
feature: GraphQL
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
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

Isso mostrará um relatório de compatibilidade. Se você tiver incompatibilidades, precisará atualizar a instância do PWA Studio ou Adobe Commerce. Verifique a [matriz de compatibilidade do Adobe Commerce](https://developer.adobe.com/commerce/pwa-studio/integrations/adobe-commerce/version-compatibility/) para ver quais versões você precisa.

Consulte a documentação a seguir para obter instruções sobre como atualizar:

* Para atualizações de PWA Studio, procure a seção &quot;Atualizando de uma versão anterior&quot; das [notas de versão de PWA](https://github.com/magento/pwa-studio/releases/) para a versão para a qual você precisa atualizar.
* [Atualize o Adobe Commerce na versão de infraestrutura na nuvem](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version) em nossa documentação do desenvolvedor
* [Atualize o Adobe Commerce local (instalado usando &quot;composer create-project&quot; ou arquivo)](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/implementation/perform-upgrade) em nossa documentação do desenvolvedor
* [Atualize o Adobe Commerce local (instalado por meio da clonagem do Adobe Commerce repo)](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/developer/git-installs) em nossa documentação do desenvolvedor

## Leitura relacionada

* [PWA Studio: o Webpack trava antes de iniciar a compilação](/help/troubleshooting/miscellaneous/pwa-studio-webpack-hangs-before-beginning-compilation.md) em nossa base de dados de conhecimento de suporte
* [PWA Studio: erros de validação ao executar o modo de desenvolvedor](/help/troubleshooting/miscellaneous/pwa-studio-validation-errors-when-running-developer-mode.md) em nossa base de dados de conhecimento de suporte
* [PWA Studio: o navegador exibe o erro &quot;Não é possível intermediar para&quot;](/help/troubleshooting/miscellaneous/pwa-studio-browser-displays-cannot-proxy-to-error.md) em nossa base de dados de conhecimento de suporte
* [Configurar o NPM para poder usar o PWA Studio](/help/how-to/general/configure-npm-to-be-able-to-use-pwa-studio.md) em nossa base de dados de conhecimento de suporte
* [PWA para a documentação do Adobe Commerce](https://magento.github.io/pwa-studio/)
