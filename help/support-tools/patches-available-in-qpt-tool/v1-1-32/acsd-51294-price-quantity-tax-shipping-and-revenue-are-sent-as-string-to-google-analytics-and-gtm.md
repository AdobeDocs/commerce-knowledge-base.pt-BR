---
title: '"ACSD-51294: Preço, quantidade, imposto, envio, receita enviada como cadeia de caracteres para [!DNL Google Analytics] e GTM'''
description: Aplique o patch ACSD-51294 para corrigir o problema do Adobe Commerce em que o preço, a quantidade, o imposto, o envio e a receita são enviados como uma sequência de caracteres para [!DNL Google Analytics] e GTM.
feature: Orders, Shipping/Delivery, Variables
role: Admin
exl-id: 159e1e98-0def-4b20-901d-f5f58c3ead7c
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# ACSD-51294: Preço, quantidade, imposto, envio, receita enviada como cadeia de caracteres para [!DNL Google Analytics] e GTM

O patch ACSD-51294 corrige o problema em que o preço, a quantidade, o imposto, o envio e a receita são enviados como uma sequência de caracteres para [!DNL Google Analytics] e GTM. Este patch está disponível quando a variável [!DNL Quality Patches Tool (QPT)] O 1.1.32 está instalado. A ID do patch é ACSD-51294. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Preço, quantidade, imposto, remessa e receita são enviados como uma sequência de caracteres para [!DNL Google Analytics] e GTM.

<u>Etapas a serem reproduzidas</u>:

1. Configurar [!DNL Google Tag Manager] navegando até **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Google API]** > **[!UICONTROL Google GTag]** > **[!UICONTROL Google Analytics4]**.
2. Crie um produto simples.
3. Conclua o check-out com esse produto.
4. Verifique a `dataLayer` Variável JavaScript na página de sucesso do check-out.

<u>Resultados esperados</u>

Os valores de preço e quantidade são numéricos.

<u>Resultados reais</u>

Os valores de preço e quantidade são uma cadeia de caracteres.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) no [!DNL Quality Patches Tool] guia.
