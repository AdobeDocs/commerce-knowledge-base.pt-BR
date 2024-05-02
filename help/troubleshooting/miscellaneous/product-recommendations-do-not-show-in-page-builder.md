---
title: O Recommendations do produto não é exibido no Page Builder
description: Este artigo fornece uma solução para o problema em que a opção Recommendations do produto não é exibida no Page Builder.
exl-id: e96a446b-2e64-47a6-ac1b-e73183da9fb8
feature: Page Builder, Configuration, Personalization, Products, Recommendations
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 0%

---

# O Recommendations do produto não é exibido no Page Builder

Este artigo fornece uma solução para o problema em que a opção Recommendations do produto não é exibida no Page Builder.

## Produtos e versões afetados

* Adobe Commerce (todos os métodos de implantação)

## Problema

A opção Recommendations do produto não é exibida no Page Builder.

## Causa

Não há opção no Page Builder para adicionar o Recommendations do produto. O Recommendations de produto do Page Builder é um módulo opcional e é instalado separadamente.

## Solução

1. Verifique se você instalou o módulo separadamente executando o comando: `composer show magento/module-page-builder-product-recommendations`
1. Se retornar a seguinte mensagem: *Pacote magento/module-page-builder-product-recommendations não encontrado*, você terá que instalá-lo executando o comando: `composer require magento/module-page-builder-product-recommendations`

Ao ativar o Recommendations do produto no Page Builder, você poderá [adicionar uma unidade de recomendação](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/add-content/recommendations.html) a qualquer conteúdo criado no Page Builder.

## Leitura relacionada

* [Adicionar conteúdo - Recommendations do produto](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/add-content/recommendations.html) em nosso guia do usuário.
* [Instalar e configurar o Recommendations do produto](https://devdocs.magento.com/recommendations/install-configure.html) na documentação do desenvolvedor.
* [Guia do usuário do Adobe Commerce](https://docs.magento.com/user-guide/)
