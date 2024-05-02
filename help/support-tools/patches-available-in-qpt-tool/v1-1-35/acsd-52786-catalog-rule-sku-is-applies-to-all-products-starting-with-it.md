---
title: '"ACSD-52786: regra de catálogo *[!UICONTROL SKU is]* aplica-se a todos os produtos que começam com o SKU'''
description: Aplique o patch ACSD-52786 para corrigir o problema do Adobe Commerce em que a condição da regra de catálogo *[!UICONTROL SKU is]* aplica-se a todos os produtos que começam com o SKU fornecido.
feature: Price Rules
role: Admin
exl-id: af373b6c-5944-412b-a544-cc6fc3f209d3
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 0%

---

# ACSD-52786: regra do catálogo &quot;*[!UICONTROL SKU is]*&quot; se aplica a todos os produtos que começam com o SKU

O patch ACSD-52786 corrige o problema em que a condição da regra de catálogo *[!UICONTROL SKU is]* se aplica a todos os produtos que começam com o SKU fornecido. Este patch está disponível quando a variável [!DNL Quality Patches Tool (QPT)] O 1.1.35 está instalado. A ID do patch é ACSD-52786. Observe que o problema foi corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5 - 2.4.5-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Condição de regra de catálogo *[!UICONTROL SKU is]* se aplica a todos os produtos que começam com o SKU fornecido.

<u>Etapas a serem reproduzidas</u>:

1. Crie dois produtos, um com o SKU &quot;24&quot; e outro com o SKU &quot;24-MB01&quot;.
1. Navegue até **[!UICONTROL Marketing]** > **[!UICONTROL Catalog Price Rule]** > **[!UICONTROL Add New Rule]**.
1. Aplique a seguinte condição:
   * *[!UICONTROL If ** TODOS **dessas condições são** TRUE **]*: *[!UICONTROL SKU is 24]*
1. Definir qualquer valor de desconto em ações.
1. Clique em **[!UICONTROL Save and Apply]**.
1. Liberar cache.
1. Acesse a loja e verifique o preço de 24-MB01.

<u>Resultados esperados</u>:

A regra de catálogo é aplicada somente a um único produto com SKU igual a 24.

<u>Resultados reais</u>:

Condição de regra de catálogo *[!UICONTROL SKU is]* se aplica a todos os produtos que começam com o SKU fornecido.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.
