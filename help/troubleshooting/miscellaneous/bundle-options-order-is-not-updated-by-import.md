---
title: A ordem de opções do pacote não é atualizada pela importação
description: Este artigo fornece uma solução para o problema que ocorre quando, após importar produtos de um arquivo .csv, as opções de pacote do produto aparecem em uma ordem diferente da listada no arquivo de importação.
exl-id: 7f7bf782-4b35-4067-aa94-417097079f1f
feature: Data Import/Export
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '212'
ht-degree: 0%

---

# A ordem de opções do pacote não é atualizada pela importação

Este artigo fornece uma solução para o problema que ocorre quando, após importar produtos de um arquivo .csv, as opções de pacote do produto aparecem em uma ordem diferente da listada no arquivo de importação.

## Produtos e versões afetados

* Adobe Commerce na infraestrutura em nuvem 2.2.x, 2.3.x
* Adobe Commerce no local 2.2.x, 2.3.x
* Magento Open Source

## Problema

<u>Pré-requisitos</u>:

Você tem um arquivo .csv válido contendo produtos agrupados.

<u>Etapas a serem reproduzidas</u>:

1. Importe o arquivo usando o [Funcionalidade de importação](https://docs.magento.com/m2/ee/user_guide/system/data-import.html).
1. Abra a página do produto do pacote.

<u>Resultados esperados</u>:

A ordem das opções é igual à do arquivo .csv.

<u>Resultados reais</u>:

A ordem das opções é diferente daquela no arquivo .csv.

## Causa

A posição das opções não foi declarada explicitamente.

## Solução

1. Declarar uma posição explicitamente para cada opção no `position` parâmetro do `bundle_values` no arquivo .csv. Para obter instruções detalhadas, consulte [Editar os dados do produto](https://docs.magento.com/m2/ee/user_guide/system/data-transfer-bundle-products.html#method-2-edit-the-product-data) em nosso guia do usuário.
1. Repita a operação de importação.

Para obter informações gerais sobre Importação, consulte a [Importando produto do pacote](https://docs.magento.com/m2/ee/user_guide/system/data-transfer-bundle-products.html) em nosso guia do usuário.
