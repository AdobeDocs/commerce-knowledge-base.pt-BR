---
title: "ACSD-51294: Preço, quantidade, imposto, remessa, receita enviada como cadeia de caracteres para [!DNL Google Analytics] e GTM"
description: Aplique o patch ACSD-51294 para corrigir o problema do Adobe Commerce em que o preço, a quantidade, o imposto, o envio e a receita são enviados como uma cadeia de caracteres para [!DNL Google Analytics] e GTM.
feature: Orders, Shipping/Delivery, Variables
role: Admin
exl-id: 159e1e98-0def-4b20-901d-f5f58c3ead7c
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# ACSD-51294: Preço, quantidade, imposto, remessa, receita enviada como cadeia de caracteres para [!DNL Google Analytics] e GTM

O patch ACSD-51294 corrige o problema em que o preço, a quantidade, o imposto, o envio e a receita são enviados como uma cadeia de caracteres para [!DNL Google Analytics] e GTM. Este patch está disponível quando o [!DNL Quality Patches Tool (QPT)] 1.1.32 está instalado. A ID do patch é ACSD-51294. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Preço, quantidade, imposto, remessa e receita são enviados como uma cadeia de caracteres para [!DNL Google Analytics] e GTM.

<u>Etapas a serem reproduzidas</u>:

1. Configure [!DNL Google Tag Manager] navegando até **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Google API]** > **[!UICONTROL Google GTag]** > **[!UICONTROL Google Analytics4]**.
2. Crie um produto simples.
3. Conclua o check-out com esse produto.
4. Verifique a variável JavaScript `dataLayer` na página de sucesso do check-out.

<u>Resultados esperados</u>

Os valores de preço e quantidade são numéricos.

<u>Resultados reais</u>

Os valores de preço e quantidade são uma cadeia de caracteres.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] versão: uma nova ferramenta para autoatender patches de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando o [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) no guia [!DNL Quality Patches Tool].
