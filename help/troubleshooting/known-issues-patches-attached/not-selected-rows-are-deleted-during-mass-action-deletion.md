---
title: Mais produtos foram excluídos do que iniciados durante a exclusão em massa no Administrador
description: Este artigo fornece um patch para o problema conhecido do Adobe СCommerce na infraestrutura em nuvem 2.2.3 relacionado à não seleção de registros que estão sendo excluídos quando uma exclusão em massa é executada em uma grade no administrador do Commerce.
exl-id: 0bfdc84e-0292-4702-a20e-bdbe67c111a2
feature: Admin Workspace, Products
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '275'
ht-degree: 0%

---

# Mais produtos foram excluídos do que iniciados durante a exclusão em massa no Administrador

Este artigo fornece um patch para o problema conhecido do Adobe СCommerce na infraestrutura em nuvem 2.2.3 relacionado à não seleção de registros que estão sendo excluídos quando uma exclusão em massa é executada em uma grade no administrador do Commerce.

## Problema

No Administrador, se você selecionar registros de cliente ou cliente a serem excluídos, filtrar a grade e selecionar a ação **Excluir**, todos os registros serão excluídos.

<u>Etapas a serem reproduzidas</u>:

1. Navegue até **Catálogo** > **Produtos** no Administrador.
1. Selecione um ou vários produtos.
1. Selecione Excluir no menu suspenso Ações.

<u>Resultados esperados</u>:

Somente os produtos selecionados são excluídos.

<u>Resultados reais</u>:

Alguns outros produtos também são excluídos.

## Correção

O patch está anexado a este artigo. Para baixá-lo, role para baixo até o final do artigo e clique no nome do arquivo ou clique no link a seguir:

[Baixar MDVA-10600\_EE\_2.2.3\_v1.composer.patch](assets/MDVA-10600_EE_2.2.3_v1.composer.patch.zip)

### Versões compatíveis do Adobe Commerce:

A correção foi criada para:

* Adobe Commerce na infraestrutura em nuvem 2.2.3

O patch também é compatível (mas pode não resolver o problema) com as seguintes versões e edições do Adobe Commerce:

* Adobe Commerce no local 2.1.8-2.1.14, 2.2.0-2.2.2 e 2.2.4-2.2.5
* Adobe Commerce na infraestrutura em nuvem 2.2.4-2.2.5

## Como aplicar o patch

Consulte [Como aplicar um patch de compositor fornecido pelo Adobe Commerce](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) para obter instruções.
