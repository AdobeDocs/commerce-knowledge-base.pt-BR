---
title: "ACSD-53309: aplicativo de imposto incompleto para opções personalizáveis e rótulo [!UICONTROL Regular Price]"
description: Aplique o patch ACSD-53309 para corrigir o problema do Adobe Commerce em que o imposto não é totalmente aplicado no rótulo '[!UICONTROL Regular Price]' quando uma opção personalizável é selecionada.
feature: Taxes, Shipping/Delivery
role: Admin, Developer
exl-id: de9b151e-6f92-4231-9e9f-4818c2961782
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---

# ACSD-53309: aplicativo de imposto incompleto para opções personalizáveis e rótulo &#39;[!UICONTROL Regular Price]&#39;

O patch ACSD-53309 corrige o problema em que o imposto não é totalmente aplicado no rótulo &#39;[!UICONTROL Regular Price]&#39; quando uma opção personalizável é selecionada. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.43 está instalado. A ID do patch é ACSD-53309. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O imposto não é totalmente refletido no rótulo &#39;[!UICONTROL Regular Price]&#39; quando uma opção personalizável é escolhida.

<u>Etapas a serem reproduzidas</u>:

1. Faça logon no Painel de administração.
1. Navegue até **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Tax]** para definir as configurações de imposto.

   * [!UICONTROL Tax Classes]:

      * [!UICONTROL Tax Class for Shipping] = [!UICONTROL Taxable Goods]
      * [!UICONTROL Tax Class for Gift Options] = [!UICONTROL Taxable Goods]

   * [!UICONTROL Calculation Settings]:

      * [!UICONTROL Catalog Prices] = [!UICONTROL Including Tax]
      * [!UICONTROL Shipping Prices] = [!UICONTROL Including Tax]
      * [!UICONTROL Apply Discount On Prices] = [!UICONTROL Including Tax]

   * [!UICONTROL Default Tax Destination Calculation]:

      * [!UICONTROL Default Post Code] = *

   * [!UICONTROL Price Display Settings]:

      * [!UICONTROL Display Product Prices In Catalog] = [!UICONTROL Including Tax]
      * [!UICONTROL Display Shipping Prices] = [!UICONTROL Including Tax]

   * [!UICONTROL Shopping Cart Display Settings]:

      * [!UICONTROL Display Prices] = [!UICONTROL Including Tax]
      * [!UICONTROL Display Subtotal] = [!UICONTROL Including Tax]
      * [!UICONTROL Display Shipping Amount] = [!UICONTROL Including Tax]

1. Conjunto **[!UICONTROL Shipping Settings]** > **[!UICONTROL Origin]** > **[!UICONTROL Country]** = *Reino Unido*.

1. Criar os seguintes *[!UICONTROL Tax Rate]* e *[!UICONTROL Tax Rules]*:

   * [!UICONTROL Country] = Estados Unidos
   * [!UICONTROL Zip Code] = *
   * [!UICONTROL State] = *
   * [!UICONTROL Rate] = 20%
1. Crie um produto simples e defina o seguinte:
   * [!UICONTROL Price = 110]
   * [!UICONTROL Special Price = 100]
   * Na lista suspensa, defina tipo como opção personalizada com preço definido como 15%
1. Vá para a página do produto do item simples feito na loja.
1. Escolha a opção personalizada criada, *15%*.

<u>Resultados esperados</u>:

* O imposto de 20% é aplicado à opção personalizada selecionada.
* &#39;[!UICONTROL Regular Price]&#39; = 151,80.

<u>Resultados reais</u>:

* O imposto de 20% não é aplicado à opção personalizada selecionada.
* &#39;[!UICONTROL Regular Price]&#39; = 148,50.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] versão: uma nova ferramenta para autoatender patches de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando o [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
