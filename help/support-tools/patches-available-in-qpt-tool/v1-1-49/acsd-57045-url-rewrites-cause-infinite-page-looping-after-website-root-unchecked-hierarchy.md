---
title: 'ACSD-57045: substituições de URL causam looping de página infinito após [!UICONTROL Website Root] ser desmarcado de [!UICONTROL Hierarchy]'
description: Aplique o patch ACSD-57045 para corrigir o problema do Adobe Commerce em que substituições de URL causam looping de página infinito depois que [!UICONTROL Website Root] é desmarcado de [!UICONTROL Hierarchy].
feature: CMS
role: Admin, Developer
exl-id: 9dca2d1a-3aef-41f0-b140-f3987003a5fd
source-git-commit: a84c3d296deb49d419be78f454696177a974d923
workflow-type: tm+mt
source-wordcount: '495'
ht-degree: 0%

---

# ACSD-57045: substituições de URL causam looping de página infinito após [!UICONTROL Website Root] ser desmarcado de [!UICONTROL Hierarchy]

O patch ACSD-57045 corrige o problema em que regravações de URL causam looping de página infinito depois que **[!UICONTROL Website Root]** é desmarcado de **[!UICONTROL Hierarchy]**. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.49 está instalado. A ID do patch é ACSD-57045. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.5.0.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5 - 2.4.6-p7

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

As substituições de URL causam looping de página infinito depois que **[!UICONTROL Website Root]** é desmarcado de **[!UICONTROL Hierarchy]**.

<u>Etapas a serem reproduzidas</u>:

1. Crie uma página do CMS chamada *Test-Parent*.
1. Crie uma página chamada *Test-Child*, e na seção **[!UICONTROL Hierarchy]**, selecione **[!UICONTROL Website Root]** > **[!UICONTROL Parent]** e salve.
1. Vá para **[!UICONTROL Marketing]** > **[!UICONTROL URL Rewrites]**.
1. Observe que há duas novas regravações:
   * Caminho de solicitação para *Test-Parent* que aponta para *cms/page/view/page_id/ID_NUMBER_FOR_PAGE*
   * Caminho de solicitação para *Test-Child* que aponta para *cms/page/view/page_id/ID_NUMBER_FOR_PAGE*
1. Visite a loja e adicione *test-child* à URL. Você deve ver a página secundária.
1. Faça a mesma coisa, mas adicione *test-parent/test-child/* à URL e veja a mesma página.
1. Vá para **[!UICONTROL Marketing]** > **[!UICONTROL URL Rewrites]** e selecione **[!UICONTROL Add URL Rewrite]**. Escolha as seguintes configurações:
   * Tipo: *Personalizado*
   * Caminho da solicitação: *test-parent/test-child*
   * Caminho de destino: *test-child*
   * Tipo de Redirecionamento: *Permanente (301)*
1. Visite o caminho *testar-pai/testar-filho* e você deverá ser redirecionado para *testar-filho*.
1. Edite a página Filho (**[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Pages]** > Escolher Filho e selecione **[!UICONTROL Edit]**).
1. Na seção **[!UICONTROL Hierarchy]**, mantenha *Test-Parent* selecionado, mas desmarque **[!UICONTROL Website Root]** e salve.
1. Vá para **[!UICONTROL Marketing]** > **[!UICONTROL URL Rewrites]** e observe que o redirecionamento original de *test-child* para *cms/page/view/page_id* está ausente e, nesse ponto, ele é substituído por um caminho que aponta o *test-child* para *test-parent/test-child*.
1. Visite a loja e tente visitar a página *Test-Child*.

<u>Resultados esperados</u>:

A página *Test-Child* está aberta.

<u>Resultados reais</u>:

A página *Test-Child* não está aberta. O navegador tenta abrir a página *test-parent/test-child* em um loop infinito.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] versão: uma nova ferramenta para autoatender patches de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando o [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
