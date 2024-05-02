---
title: '"ACSD-49129: o atributo "Conteúdo" não é retornado nas respostas da API de mídia do produto"'
description: Aplique o patch ACSD-49129 para corrigir o problema do Adobe Commerce em que o atributo *content* (*código de imagem base64*) não é retornado nas respostas da API de mídia do produto "rest/V1/products/sku/media".
exl-id: b7022046-3f52-4880-81b8-977ed270773f
feature: REST, Attributes, Media, Page Content, Products
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '347'
ht-degree: 0%

---

# ACSD-49129: o atributo &quot;Conteúdo&quot; não é retornado nas respostas da API de mídia do produto

O patch ACSD-49129 corrige o problema em que a variável *conteúdo* atributo (*[!UICONTROL base64 image code]*) não é retornado na variável `rest/V1/products/sku/media` respostas da API de mídia do produto. Este patch está disponível quando a variável [!DNL Quality Patches Tool (QPT)] O 1.1.30 está instalado. A ID do patch é ACSD-49129. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3-p3

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2 - 2.4.5-p2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A variável *conteúdo* atributo (*[!UICONTROL base64 image code]*) não é retornado na variável `rest/V1/products/sku/media` respostas da API de mídia do produto.

<u>Etapas a serem reproduzidas</u>:

1. Crie um produto com uma imagem.
1. Enviar *API DO GET* solicitação para `rest/V1/products/<sku>/media` e `rest/V1/products/<sku>/media/<entryId>`.
1. Verifique as respostas da API.

<u>Resultados esperados</u>

A variável *conteúdo* O atributo com os dados está disponível por meio da API REST.

<u>Resultados reais</u>

A variável *conteúdo* O atributo não está presente nas respostas da API.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.
