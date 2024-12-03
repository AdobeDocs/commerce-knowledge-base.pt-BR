---
title: 'ACSD-50621: os preços de nível para diferentes sites no catálogo compartilhado não estão visíveis'
description: Aplique o patch ACSD-50621 para corrigir o problema do Adobe Commerce, em que os preços de camada para sites diferentes no catálogo compartilhado não estão visíveis ao editá-los em um ambiente de vários sites.
exl-id: 6d6635bc-4f76-4e2f-9bc7-0276cced8ca9
feature: Catalog Management, Orders
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---

# ACSD-50621: os preços de nível para diferentes sites no catálogo compartilhado não estão visíveis

O patch ACSD-50621 corrige o problema em que os preços de nível para sites diferentes no catálogo compartilhado não estão visíveis ao editá-los em um ambiente de vários sites. Este patch está disponível quando o [!DNL Quality Patches Tool (QPT)] 1.1.32 está instalado. A ID do patch é ACSD-50621. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.7 - 2.4.6

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os preços de nível para diferentes sites no catálogo compartilhado não ficam visíveis ao editá-los em um ambiente de vários sites.

<u>Etapas a serem reproduzidas</u>:

1. Defina o **[!UICONTROL Catalog Price Scope]** como **[!UICONTROL Website]**.
1. Crie um site, loja e loja adicionais.
1. Crie um produto simples e o atribua a todos os sites.
1. Crie um catálogo compartilhado personalizado.
1. Vá para **[!UICONTROL Set Pricing and Structure]** para obter o catálogo compartilhado personalizado que você criou.
1. Na Etapa 1: selecione produtos para catálogo. Adicione o produto simples que você criou.
1. Na etapa 2: defina preços personalizados e clique em **[!UICONTROL Configure]**.
1. Defina preços de camada diferentes para sites diferentes.
1. Selecione **[!UICONTROL Done]**, clique em **[!UICONTROL Generate Catalog]** e em **[!UICONTROL Save]**.
1. Execute o cron.
1. Navegue até **[!UICONTROL Set Pricing and Structure]** > **[!UICONTROL Configure]** > **[!UICONTROL Next]** > **[!UICONTROL Configure]** e verifique o preço da camada.

<u>Resultados esperados</u>:

Todos os preços de camada configurados anteriormente para diferentes sites estão presentes.

<u>Resultados reais</u>:

Os preços de nível que foram configurados anteriormente não estão presentes.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] versão: uma nova ferramenta para autoatender patches de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando o [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
