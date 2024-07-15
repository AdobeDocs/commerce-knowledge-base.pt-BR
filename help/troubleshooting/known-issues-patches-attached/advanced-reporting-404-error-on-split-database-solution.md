---
title: Erro 404 do Advanced Reporting na solução de banco de dados dividido
description: Este artigo fornece um patch para usuários do Adobe Commerce 2.3.x com a [solução de banco de dados dividido](https://devdocs.magento.com/guides/v2.3/config-guide/multi-master/multi-master.html) que enfrentam um erro 404 ao tentar usar o Relatórios avançados.
exl-id: b81d4ada-5f38-4882-bc5b-ab4ccd63fc5f
feature: Commerce Intelligence
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '171'
ht-degree: 0%

---

# Erro 404 do Advanced Reporting na solução de banco de dados dividido

Este artigo fornece um patch para usuários do Adobe Commerce 2.3.x com a [solução de banco de dados dividido](https://devdocs.magento.com/guides/v2.3/config-guide/multi-master/multi-master.html) que experimentam um erro 404 ao tentar usar o Relatórios Avançados.

## Produtos e versões afetados

Adobe Commerce 2.3.0 - 2.3.5-p1

## Problema

O patch corrige o problema em que o nome de conexão errado é usado para coletar dados de aspas. Devido ao nome de conexão incorreto estar sendo usado, os dados da cotação não são enviados para o Magento Business Intelligence (MBI) e os relatórios não podem ser gerados.

## Solução

Aplique o [patch](assets/MDVA-26831_EE_2.3.4_v1.composer.patch.zip) fornecido neste artigo.

## Correção

O patch está anexado a este artigo. Para baixá-lo, clique no link a seguir:

[MDVA-26831\_EE\_2.3.4\_v1.composer.patch](assets/MDVA-26831_EE_2.3.4_v1.composer.patch.zip)

## Como aplicar o patch

Descompacte o arquivo e siga as instruções em [Como aplicar um patch de compositor fornecido pelo Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md).
