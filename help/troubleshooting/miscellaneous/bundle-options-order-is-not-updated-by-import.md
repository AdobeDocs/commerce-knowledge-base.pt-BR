---
title: A ordem de opções do pacote não é atualizada pela importação
description: Este artigo fornece uma solução para o problema que ocorre quando, após importar produtos de um arquivo .csv, as opções de pacote do produto aparecem em uma ordem diferente da listada no arquivo de importação.
exl-id: 7f7bf782-4b35-4067-aa94-417097079f1f
feature: Data Import/Export
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
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

1. Importe o arquivo usando a [funcionalidade de importação](https://experienceleague.adobe.com/pt-br/docs/commerce-admin/systems/data-transfer/import/data-import).
1. Abra a página do produto do pacote.

<u>Resultados esperados</u>:

A ordem das opções é igual à do arquivo .csv.

<u>Resultados reais</u>:

A ordem das opções é diferente daquela no arquivo .csv.

## Causa

A posição das opções não foi declarada explicitamente.

## Solução

1. Declare uma posição explicitamente para cada opção no parâmetro `position` da coluna `bundle_values` no arquivo .csv. Para obter instruções detalhadas, consulte [Editar os dados do produto](https://experienceleague.adobe.com/pt-br/docs/commerce-admin/systems/data-transfer/examples/data-transfer-bundle-products#method-2-edit-the-product-data) no guia do usuário.
1. Repita a operação de importação.

Para obter informações gerais sobre Importação, consulte o [Produto do Pacote de Importação](https://experienceleague.adobe.com/pt-br/docs/commerce-admin/systems/data-transfer/examples/data-transfer-bundle-products) no nosso guia do usuário.
