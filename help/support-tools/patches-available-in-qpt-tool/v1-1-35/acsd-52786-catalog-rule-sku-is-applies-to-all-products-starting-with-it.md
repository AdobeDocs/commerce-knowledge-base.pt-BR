---
title: 'ACSD-52786: a regra de catálogo *[!UICONTROL SKU is]* se aplica a todos os produtos que começam com a SKU'
description: Aplique o patch ACSD-52786 para corrigir o problema do Adobe Commerce em que a condição de regra de catálogo *[!UICONTROL SKU is]* se aplica a todos os produtos que começam com o SKU fornecido.
feature: Price Rules
role: Admin
exl-id: af373b6c-5944-412b-a544-cc6fc3f209d3
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 0%

---

# ACSD-52786: a regra de catálogo &quot;*[!UICONTROL SKU is]*&quot; se aplica a todos os produtos que começam com a SKU

O patch ACSD-52786 corrige o problema em que a condição de regra de catálogo *[!UICONTROL SKU is]* se aplica a todos os produtos que começam com a SKU fornecida. Este patch está disponível quando o [!DNL Quality Patches Tool (QPT)] 1.1.35 está instalado. A ID do patch é ACSD-52786. Observe que o problema foi corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5 - 2.4.5-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A condição de regra de catálogo *[!UICONTROL SKU is]* se aplica a todos os produtos que começam com a SKU fornecida.

<u>Etapas a serem reproduzidas</u>:

1. Crie dois produtos, um com o SKU &quot;24&quot; e outro com o SKU &quot;24-MB01&quot;.
1. Navegue até **[!UICONTROL Marketing]** > **[!UICONTROL Catalog Price Rule]** > **[!UICONTROL Add New Rule]**.
1. Aplique a seguinte condição:
   * *[!UICONTROL If **&#x200B; TODAS &#x200B;** destas condições são **&#x200B; TRUE &#x200B;**]*: *[!UICONTROL SKU is 24]*
1. Definir qualquer valor de desconto em ações.
1. Clique em **[!UICONTROL Save and Apply]**.
1. Liberar cache.
1. Acesse a loja e verifique o preço de 24-MB01.

<u>Resultados esperados</u>:

A regra de catálogo é aplicada somente a um único produto com SKU igual a 24.

<u>Resultados reais</u>:

A condição de regra de catálogo *[!UICONTROL SKU is]* se aplica a todos os produtos que começam com a SKU fornecida.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] versão: uma nova ferramenta para autoatender patches de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando o [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
