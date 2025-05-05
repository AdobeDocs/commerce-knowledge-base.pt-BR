---
title: Erro  [!DNL opensearch] o mecanismo de pesquisa não existe. Retornando para  [!DNL livesearch].
description: Este artigo fornece uma solução para o problema em que você vê o erro, 'Erro- [!DNL opensearch] mecanismo de pesquisa não existe. Retornando para  [!DNL livesearch].&grave;, no Adobe Commerce na infraestrutura em nuvem.
feature: Deploy, Search
role: Developer
exl-id: a6cc981d-b8f0-402d-8771-60d2f21f09f8
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '153'
ht-degree: 0%

---

# Erro [!DNL opensearch] mecanismo de pesquisa não existe. Retornando para [!DNL livesearch].

Este artigo fornece uma solução para o problema em que você vê o erro: *Erro: [!DNL opensearch] o mecanismo de pesquisa não existe. Retornando para [!DNL livesearch].* no Adobe Commerce na infraestrutura em nuvem, onde [!DNL Live Search] é usado.

## Produtos e versões afetados

* Adobe Commerce na infraestrutura em nuvem, todas as versões
* [!DNL Live Search] está instalado e em uso

## Problema

A seguinte mensagem é mostrada nos logs (e pode ser observada em [!DNL New Relic]):
*Erro: [!DNL opensearch] mecanismo de pesquisa não existe. Retornando para [!DNL livesearch].*

## Solução

1. Modifique o arquivo `.magento.env.yaml`.
1. Localize as seguintes linhas:

   ```yaml
     deploy:
   ...
       SEARCH_CONFIGURATION:
         engine: opensearch
   ```

1. Se você não tiver essas linhas, adicione-as ao arquivo `.magento.env.yaml`.
1. Se estas linhas existirem, **modifique o mecanismo** de *[!DNL opensearch]* para *[!DNL livesearch]*.
1. Confirme a alteração e implante novamente.

## Leitura relacionada

* [Instalar [!DNL Live Search]](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html) em nosso Guia do Live Search
