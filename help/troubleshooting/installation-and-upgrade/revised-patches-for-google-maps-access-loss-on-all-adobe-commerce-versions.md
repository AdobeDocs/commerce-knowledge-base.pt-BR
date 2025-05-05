---
title: Patches revisados para perda de acesso ao Google Maps em todas as versões do Adobe Commerce
description: 'Este artigo fornece uma correção para comerciantes do Adobe Commerce que não são compatíveis com nenhuma versão  [!DNL Google Maps]  recente da 3.54+.'
feature: Install, Upgrade
role: Developer
source-git-commit: cf235c2fdd7a36d7e3b126de35c51e6711cd3845
workflow-type: tm+mt
source-wordcount: '313'
ht-degree: 0%

---

# Patches revisados para [!DNL Google Maps] perda de acesso em todas as versões do Adobe Commerce

Este artigo fornece uma correção para comerciantes do Adobe Commerce que não são compatíveis com nenhuma versão recente do [!DNL Google Maps] da versão 3.54+. Essa correção é para resolver o problema em que os comerciantes do Adobe Commerce não têm mais acesso ao [!DNL Google Maps] em nenhuma versão do Adobe Commerce.

## Versões e produtos afetados

* Versões do Adobe Commerce e/ou outras tecnologias usadas.
* Adobe Commerce *2.4.4* - *2.4.7* nas versões em nuvem e no local.

## Problema

Em *14 de junho de 2024* a versão *3.53* do [!DNL Google Maps] chegou ao fim da vida útil e foi desligada por [!DNL Google].

Para obter mais informações, consulte [[!DNL Google Maps Platform: Maps JavaScript API]](https://developers.google.com/maps/documentation/javascript/versions#documentation-for-the-api-versions).

O Adobe Commerce não era compatível com nenhuma versão recente do [!DNL &#x200B; Google Maps] da versão 3.54+.

A incompatibilidade foi causada por `prototype.js script` herdado, que carregado por meio de `lib/web/legacy-build.min.js` substitui a função Array.from nativa, o que leva a um conflito direto com a API [!DNL &#x200B; Google Maps].

Consulte [[!DNL Google Maps: JS Best Practices]](https://developers.google.com/maps/documentation/javascript/best-practices).

<u>Etapas a serem reproduzidas</u>:

1. Clique em **[!UICONTROL Content]** > **[!UICONTROL Pages]** > e selecione um **[!UICONTROL New Page]**.
1. Expanda o Bloco de Conteúdo e clique no botão editar **[!DNL PageBuilder]**.
1. Arraste o Bloco de Conteúdo de Mapa do menu **[!DNL PageBuilder]** para a página.

<u>Resultado esperado:</u>

[!DNL Google Maps] deve funcionar conforme esperado.

<u> Resultado real:</u>

Ao soltar o Bloco de Conteúdo de Mapa do menu **[!DNL PageBuilder]** na página, uma mensagem de erro como *&quot;Desculpe! Algo deu errado.&quot;* é exibido.

## Solução

* Todos os comerciantes em qualquer versão de patch 2.4.4, 2.4.5, 2.4.6 ou 2.4.7 devem aplicar esses patches correspondentes à sua versão.

## Correção

Use os seguintes patches anexados, dependendo da versão do Adobe Commerce:

**Para as versões 2.4.4:**
[ACSD-60245_Google_maps_API_2.4.4_2.4.5_2.4.6_composer.patch.zip](assets/ACSD-60245_Google_maps_API_2.4.4_2.4.5_2.4.6_composer.patch.zip)

**Para versões 2.4.5:**
[ACSD-60245_Google_maps_API_2.4.4_2.4.5_2.4.6_composer.patch.zip](assets/ACSD-60245_Google_maps_API_2.4.4_2.4.5_2.4.6_composer.patch.zip)

**Para versões 2.4.6:**
[ACSD-60245_Google_maps_API_2.4.4_2.4.5_2.4.6_composer.patch.zip](assets/ACSD-60245_Google_maps_API_2.4.4_2.4.5_2.4.6_composer.patch.zip)

**Para versões 2.4.7:**
[ACSD-60245_Google_maps_API_2.4.7_composer.patch.zip](assets/ACSD-60245_Google_maps_API_2.4.7_composer.patch.zip)

**Observação**

Este problema será corrigido permanentemente no escopo das versões de patch somente de segurança de agosto:
2.4.7-p2, 2.4.6-p7, 2.4.5-p9, 2.4.4-p10

## Leitura relacionada

[Como aplicar um patch de compositor fornecido pelo Adobe](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento)