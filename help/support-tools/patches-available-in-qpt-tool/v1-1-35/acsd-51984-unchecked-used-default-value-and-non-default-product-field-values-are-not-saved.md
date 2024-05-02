---
title: '"ACSD-51984: desmarcado [!UICONTROL Use Default Value] os valores de campo de produto e não padrão não são salvos para a segunda exibição de site, loja e loja'''
description: Aplique o patch ACSD-51984 para corrigir o problema do Adobe Commerce em que a opção [!UICONTROL Use Default Value] Os valores de campo de produto e não padrão não são salvos para a segunda exibição de site, loja e loja.
feature: Products
role: Admin
exl-id: 1f45c700-dd27-4a69-8634-9c0aa131d197
source-git-commit: f42fcacbe3b7174b2a3571afe80f5eedb8e9aa75
workflow-type: tm+mt
source-wordcount: '435'
ht-degree: 0%

---

# ACSD-51984: desmarcado *[!UICONTROL Use Default Value]* os valores de campo de produto e não padrão não são salvos

>[!NOTE]
>
>Este patch está desatualizado e foi substituído pelo [ACSD-54776](/help/support-tools/patches-available-in-qpt-tool/v1-1-39/acsd-54776-unchecked-used-default-value-and-non-default-product-field-values-are-not-saved.md) correção adicionada na versão 1.1.39 QPT.

O patch ACSD-51984 corrige o problema em que a variável desmarcada **[!UICONTROL Use Default Value]** Os valores de campo de produto e não padrão não são salvos para a segunda exibição de site, loja e loja. Este patch está disponível quando a variável [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.35 está instalado. A ID do patch é ACSD-51984. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Desmarcado *[!UICONTROL Use Default Value]* Os valores de campo de produto e não padrão não são salvos para a segunda exibição de site, loja e loja.

<u>Etapas a serem reproduzidas</u>:

1. Vá para o back-end e acesse **[!UICONTROL Stores]** > **[!UICONTROL All Stores]** e criar uma nova visualização de site, loja e loja.
1. Ir para **[!UICONTROL Catalog]** > **[!UICONTROL Products]**, crie um produto simples, salve-o e atribua o produto a ambos os sites pela **[!UICONTROL Product in Websites]**.
1. Altere o escopo da etapa 2 para a exibição de armazenamento recém-criada.
1. Ir para **[!UICONTROL Search Engine Optimization]** e desmarque a opção **[!UICONTROL Use Default Value]** caixas de seleção para [!UICONTROL Meta Title], [!UICONTROL Meta Keywords], e [!UICONTROL Meta Description].
1. Limpe o texto dos campos: *[!UICONTROL Meta Title]*, *[!UICONTROL Meta Keywords]* e *[!UICONTROL Meta Description]* e clique em **[!UICONTROL Save]**.
1. Ir para **[!UICONTROL Search Engine Optimization]** novamente.

<u>Resultados esperados</u>

Os valores dos campos e das caixas de seleção são salvos.

<u>Resultados reais</u>

Os valores dos campos e das caixas de seleção não são salvos.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) no [!DNL Quality Patches Tool] guia.