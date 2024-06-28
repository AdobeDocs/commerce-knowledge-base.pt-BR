---
title: Patches revisados para perda de acesso ao Google Maps em todas as versões do Adobe Commerce
description: "Este artigo fornece uma correção para os comerciantes do Adobe Commerce que não são compatíveis com qualquer [!DNL Google Maps] 3.54+."
feature: Install, Upgrade
role: Developer
source-git-commit: 575fce2f678321ff184779895d43be90828c2ce4
workflow-type: tm+mt
source-wordcount: '313'
ht-degree: 0%

---

# Patches revisados para [!DNL Google Maps] perda de acesso em todas as versões do Adobe Commerce

Este artigo fornece uma correção para comerciantes do Adobe Commerce que não são compatíveis com qualquer [!DNL Google Maps] versões da 3.54+. Essa correção é para resolver o problema em que os comerciantes do Adobe Commerce não têm acesso ao [!DNL Google Maps] em qualquer versão do Adobe Commerce.

## Versões e produtos afetados

* Versões do Adobe Commerce e/ou outras tecnologias usadas.
* Adobe Commerce *2.4.4* - *2.4.7* em versões na nuvem e no local.

## Problema

Ligado *14 de junho de 2024* [!DNL Google Maps] version *3,53* chegou ao fim da vida útil e foi desligado por [!DNL Google].

[Para obter mais informações, consulte ([!DNL Google Maps Platform: Maps JavaScript API])] (https://developers.google.com/maps/documentation/javascript/versions#documentation-for-the-api-versions).

O Adobe Commerce não era compatível com nenhum [!DNL  Google Maps] versões da 3.54+.

A incompatibilidade foi causada por versões herdadas `prototype.js script`, que carregou por meio de `lib/web/legacy-build.min.js` substitui a função Array.from nativa, o que gera um conflito direto com [!DNL  Google Maps] API.

[Consulte ([!DNL Google Maps: JS Best Practices])] (https://developers.google.com/maps/documentation/javascript/best-practices).

<u>Etapas a serem reproduzidas</u> :

1. Clique em **[!UICONTROL Content]** > **[!UICONTROL Pages]** > e selecione um **[!UICONTROL New Page]**.
1. Expanda o Bloco de conteúdo e clique no botão de edição **[!DNL PageBuilder]** botão.
1. Arraste o Bloco de Conteúdo do Mapa da **[!DNL PageBuilder]** menu para página.

<u>Resultado esperado:</u>

[!DNL Google Maps] deve funcionar conforme esperado.

<u> Resultado real:</u>

Ao soltar o Bloco de Conteúdo de Mapa de **[!DNL PageBuilder]** para a página, uma mensagem de erro como *&quot;Desculpe! Algo deu errado&quot;* é exibido.

## Solução

* Todos os comerciantes em qualquer versão de patch 2.4.4, 2.4.5, 2.4.6 ou 2.2.7 devem aplicar esses patches correspondentes à sua versão.

## Correção

Use os seguintes patches anexados, dependendo da versão do Adobe Commerce:

**Para as versões 2.4.4:**
[ACSD-60245_Google_maps_API_2.4.4_2.4.5_2.4.6_composer.patch.zip](assets/ACSD-60245_Google_maps_API_2.4.4_2.4.5_2.4.6_composer.patch.zip)

**Para as versões 2.4.5:**
[ACSD-60245_Google_maps_API_2.4.4_2.4.5_2.4.6_composer.patch.zip](assets/ACSD-60245_Google_maps_API_2.4.4_2.4.5_2.4.6_composer.patch.zip)

**Para as versões 2.4.6:**
[ACSD-60245_Google_maps_API_2.4.4_2.4.5_2.4.6_composer.patch.zip](assets/ACSD-60245_Google_maps_API_2.4.4_2.4.5_2.4.6_composer.patch.zip)

**Para as versões 2.4.7:**
[ACSD-60245_Google_maps_API_2.4.7_composer.patch.zip](assets/ACSD-60245_Google_maps_API_2.4.7_composer.patch.zip)

**Observe que**

Este problema será corrigido permanentemente no escopo das versões de patch somente de segurança de agosto: 2.4.7-p2, 2.4.6-p7, 2.4.5-p9, 2.4.4-p10

## Leitura relacionada

[Como aplicar um patch de compositor fornecido pelo Adobe](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento)