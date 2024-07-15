---
title: "ACSD-48404: *[!UICONTROL Remember Category Pagination] = [!UICONTROL Yes]* causa erro ao pressionar o botão Voltar do navegador"
description: Aplique o patch ACSD-48404 para corrigir o problema do Adobe Commerce em que *[!UICONTROL Remember Category Pagination] = [!UICONTROL Yes]* causa um erro ao pressionar o botão Voltar do navegador.
exl-id: b4b96198-dee6-4b3c-b60a-0983ef8ef7b2
feature: Categories
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '357'
ht-degree: 0%

---

# ACSD-48404: *[!UICONTROL Remember Category Pagination]=[!UICONTROL Yes]* causa erro ao pressionar o botão Voltar do navegador

O patch ACSD-48404 corrige o problema em que *[!UICONTROL Remember Category Pagination]=[!UICONTROL Yes]* causa um erro ao pressionar o botão Voltar do navegador. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.27 está instalado. A ID do patch é ACSD-48404. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3-p3

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.0 - 2.4.3-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

*[!UICONTROL Remember Category Pagination]=[!UICONTROL Yes]* causa um erro ao pressionar o botão Voltar do navegador.


<u>Etapas a serem reproduzidas</u>:

1. Vá para **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Storefront]** e defina *[!UICONTROL Remember Category Pagination]* como *Sim*.
1. Abra uma categoria na loja.
1. Selecione um valor que não seja o valor padrão na lista suspensa *[!UICONTROL Show Per Page]*. Após selecionar uma opção, a página é recarregada.
1. Depois que a página for recarregada, clique em qualquer produto na página do catálogo.
1. Na página de detalhes do produto aberta, clique no botão **[!UICONTROL Back]** do navegador.

<u>Resultados esperados</u>:

A página do catálogo é aberta novamente.

<u>Resultados reais</u>:

A página de categoria retorna um erro.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] versão: uma nova ferramenta para autoatender patches de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando o [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
