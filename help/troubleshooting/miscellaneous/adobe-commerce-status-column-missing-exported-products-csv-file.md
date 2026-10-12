---
title: Coluna de status do Adobe Commerce sem o arquivo CSV de produtos exportados
description: Este artigo fornece uma solução para o problema que ocorre quando não é possível localizar a coluna de status no arquivo CSV que contém os produtos exportados.
exl-id: 3cbe1e6c-fc73-4331-add7-1ebcb28a4580
feature: Data Import/Export, Products
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 601e4abe-d9bf-58de-a779-32ed6794dcbe
    internal-label: Data Import/Export
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 0%
---
# Coluna de status do Adobe Commerce sem o arquivo CSV de produtos exportados

Este artigo fornece uma solução para o problema quando não é possível localizar a coluna de status (ou seja, indicando se o produto está ativado ou desativado) no arquivo CSV que contém os produtos exportados. O status do produto é indicado pela coluna [!UICONTROL product_online].

## Produtos e versões afetados

Adobe Commerce (todos os métodos de implantação) todas as [versões com suporte](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## Problema

Você não pode localizar a coluna [!UICONTROL status] no arquivo CSV que contém produtos exportados. Assim, por exemplo, você exporta um CSV de todos os SKUs, com seus status, mas a tabela parece não ter a coluna [!UICONTROL status].

<u>Etapas a serem reproduzidas:</u>

1. No Administrador do Adobe Commerce, selecione **[!UICONTROL System]**, em **[!UICONTROL Data Transfer]**, selecione **[!UICONTROL Export]**.
1. Na seção **[!UICONTROL Export Settings]**, selecione no menu suspenso **[!UICONTROL Products]** de **[!UICONTROL Entity Type]**.
1. Pesquisa por **[!UICONTROL status]**, listada em **[!UICONTROL Attribute Code]**. Você vê esse código de atributo na lista de atributos disponíveis (**[!UICONTROL Enable Product]**).
1. Clique em **[!UICONTROL Export]**.

<u>Resultado esperado:</u>

No arquivo CSV que você acabou de exportar, você verá uma coluna rotulada [!UICONTROL status].

<u>Resultado real:</u>

Você não vê uma coluna rotulada [!UICONTROL status] no arquivo csv exportado.

## Causa

O atributo de status do produto foi renomeado no arquivo CSV. Agora é a coluna [!UICONTROL product_online].

## Solução

1. Selecione **[!UICONTROL System]**, em **[!UICONTROL Data Transfer]**, selecione **[!UICONTROL Import]**.
1. Clique em **[!UICONTROL Download Sample File]**.
1. Você pode ver a coluna [!UICONTROL product_online] no arquivo CSV.

## Leitura relacionada

* [Trabalhando com arquivos CSV](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-csv) em nosso guia do usuário.
* [Referência a atributos de exportação do produto](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-attributes-product) em nosso guia do usuário.
