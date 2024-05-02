---
title: "ACSD-45675: a exportação de produtos usa nomes de categoria do escopo de exibição de loja padrão"
description: O patch ACSD-45675 corrige o problema em que a exportação de produto usa nomes de categoria do escopo de exibição de loja padrão. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.20 está instalada. A ID do patch é ACSD-45675. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.
exl-id: 9edd718e-4c0c-44dd-b802-07c9ec7c182a
feature: Categories, Data Import/Export, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# ACSD-45675: a exportação de produtos usa nomes de categoria do escopo de exibição de loja padrão

O patch ACSD-45675 corrige o problema em que a exportação de produto usa nomes de categoria do escopo de exibição de loja padrão. Este patch está disponível quando a variável [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.20 está instalado. A ID do patch é ACSD-45675. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.0 - 2.4.5

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A exportação de produtos usa nomes de categorias do escopo de exibição de loja padrão.

<u>Etapas a serem reproduzidas</u>:

1. Criar uma exibição de loja personalizada **[!UICONTROL Thai]** dentro da loja principal.
1. Marca **[!UICONTROL Thai]** a visualização de loja padrão do site principal.
1. Crie a seguinte estrutura de categoria em **[!UICONTROL Default Category]**:

   *[!UICONTROL Default category/Tea/Black]*

1. Selecione a categoria **[!UICONTROL Tea]** e altere o **[!UICONTROL Scope]** para **[!UICONTROL Thai]**.
1. Defina o **[!UICONTROL Category Name]** as **[!UICONTROL ชาดำ]**.
1. Criar um produto simples **[!UICONTROL SP001]** e atribua a categoria **[!UICONTROL Black]**.
1. Certifique-se de que o cron não seja executado.
1. Fazer uma exportação de produto. Filtrar por SKU e selecionar **[!UICONTROL SP001]**.
1. Verifique a **[!UICONTROL categories]** no CSV exportado.

<u>Resultados esperados</u>:

Como nenhum armazenamento foi selecionado durante a exportação, você deve obter um caminho de categoria como o seguinte: *[!UICONTROL Default Category/Tea/Black]*.

<u>Resultados reais</u>:

O caminho da categoria tem idiomas mistos: *[!UICONTROL Default Category/ชาดำ/Black]*.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tools] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) na guia Ferramenta de correções de qualidade.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/check-patch-for-magento-issue-with-magento-quality-patches.html) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no [!DNL QPT], consulte [Patches disponíveis em [!DNL QPT]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) na guia Ferramenta de correções de qualidade.
