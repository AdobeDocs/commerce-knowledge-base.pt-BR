---
title: "ACSD-47803: amostras de produtos configuráveis indisponíveis exibidas como disponíveis"
description: Aplique o patch ACSD-47803 para corrigir o problema do Adobe Commerce em que as amostras de produto configuráveis e indisponíveis são exibidas como disponíveis.
exl-id: 28b3f378-a790-4af6-9627-5bd8571523fd
feature: Configuration, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# ACSD-47803: amostras de produtos configuráveis indisponíveis exibidas como disponíveis

O patch ACSD-47803 corrige o problema em que amostras de produtos configuráveis e indisponíveis são exibidas como disponíveis. Este patch está disponível quando a variável [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.24 está instalado. A ID do patch é ACSD-47803. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

As amostras de produtos configuráveis indisponíveis são exibidas como disponíveis.

<u>Etapas a serem reproduzidas</u>:

>[!NOTE]
>
>As etapas abaixo se referem a dados de amostra como exemplo.

1. No [!UICONTROL Commerce] Administrador, acesse **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Stock Options]** e defina o **[!UICONTROL Display Out of Stock Products]** para *Sim*.
1. Novamente, em Admin, acesse **[!UICONTROL Catalog]** > **[!UICONTROL Products]** e edite um produto configurável na página de edição do produto (por exemplo, SKU &quot;WB04&quot;, se estiver usando dados de amostra):
   * Para uma das variantes de configuração, defina a quantidade como *0* (por exemplo, para &quot;WB04-M-Roxo&quot;).
1. Agora abra o produto configurável na loja.
1. Selecione o tamanho do produto da variante configurável com zero estoque (ou seja, &quot;M&quot;).

<u>Resultados esperados</u>:

As opções indisponíveis estão desativadas e marcadas como [!UICONTROL Out of Stock].

<u>Resultados reais</u>:

Todas as amostras de cores estão habilitadas, mesmo a que está [!UICONTROL Out of Stock].

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.
