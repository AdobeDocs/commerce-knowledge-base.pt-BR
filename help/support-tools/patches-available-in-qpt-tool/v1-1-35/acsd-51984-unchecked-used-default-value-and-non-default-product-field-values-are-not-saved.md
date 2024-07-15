---
title: "ACSD-51984: desmarcado [!UICONTROL Use Default Value] e valores de campo de produto não padrão não são salvos para a segunda exibição de site, loja e loja"
description: Aplique o patch ACSD-51984 para corrigir o problema do Adobe Commerce em que os valores de campo de produto desmarcados [!UICONTROL Use Default Value] e não padrão não são salvos para a segunda exibição de site, loja e loja.
feature: Products
role: Admin
exl-id: 1f45c700-dd27-4a69-8634-9c0aa131d197
source-git-commit: f42fcacbe3b7174b2a3571afe80f5eedb8e9aa75
workflow-type: tm+mt
source-wordcount: '435'
ht-degree: 0%

---

# ACSD-51984: desmarcado *[!UICONTROL Use Default Value]* e os valores de campo de produto não padrão não são salvos

>[!NOTE]
>
>Este patch está desatualizado e foi substituído pelo patch [ACSD-54776](/help/support-tools/patches-available-in-qpt-tool/v1-1-39/acsd-54776-unchecked-used-default-value-and-non-default-product-field-values-are-not-saved.md) adicionado na versão 1.1.39 do QPT.

O patch ACSD-51984 corrige o problema em que os valores de campo de produto desmarcados **[!UICONTROL Use Default Value]** e não padrão não são salvos para a segunda exibição de site, loja e loja. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.35 está instalado. A ID do patch é ACSD-51984. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os valores de campo de produto *[!UICONTROL Use Default Value]* e não padrão desmarcados não são salvos no segundo site, loja e visualização de loja.

<u>Etapas a serem reproduzidas</u>:

1. Vá para o back-end e navegue até **[!UICONTROL Stores]** > **[!UICONTROL All Stores]** e crie um novo site, loja e modo de exibição de loja.
1. Vá para **[!UICONTROL Catalog]** > **[!UICONTROL Products]**, crie um produto simples e salve-o e atribua o produto a ambos os sites, a partir do **[!UICONTROL Product in Websites]**.
1. Altere o escopo da etapa 2 para a exibição de armazenamento recém-criada.
1. Vá para **[!UICONTROL Search Engine Optimization]** e desmarque as caixas de seleção **[!UICONTROL Use Default Value]** para [!UICONTROL Meta Title], [!UICONTROL Meta Keywords] e [!UICONTROL Meta Description].
1. Limpe o texto dos campos: *[!UICONTROL Meta Title]*, *[!UICONTROL Meta Keywords]* e *[!UICONTROL Meta Description]*, e clique em **[!UICONTROL Save]**.
1. Vá para **[!UICONTROL Search Engine Optimization]** novamente.

<u>Resultados esperados</u>

Os valores dos campos e das caixas de seleção são salvos.

<u>Resultados reais</u>

Os valores dos campos e das caixas de seleção não são salvos.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] versão: uma nova ferramenta para autoatender patches de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando o [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) no guia [!DNL Quality Patches Tool].