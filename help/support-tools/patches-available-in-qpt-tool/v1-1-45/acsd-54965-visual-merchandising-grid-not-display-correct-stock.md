---
title: '"ACSD-54965: [!UICONTROL Visual Merchandising] a grade não exibe o estoque correto'''
description: Aplique o patch ACSD-54965 para corrigir o problema do Adobe Commerce em que o [!UICONTROL Visual Merchandising] a grade não exibe o estoque correto quando um produto é atribuído ao estoque personalizado.
feature: Merchandising, Categories
role: Admin, Developer
exl-id: 13d98f55-ca2c-4064-b66f-ab2cdeb37382
source-git-commit: 4f05117aa42dec1f56e4986ffd22d1a68bf5cea2
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# ACSD-54965: [!UICONTROL Visual Merchandising] a grade não exibe o estoque correto

O patch ACSD-54965 corrige o problema em que a variável [!UICONTROL Visual Merchandising] a grade não exibe o estoque correto quando um produto é atribuído ao estoque personalizado. Este patch está disponível quando a variável [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.45 está instalado. A ID do patch é ACSD-54965. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5 - 2.4.5-p5

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A variável [!UICONTROL Visual Merchandising] a grade não exibe o estoque correto quando um produto é atribuído ao estoque personalizado.

<u>Etapas a serem reproduzidas</u>:

1. Crie uma nova fonte.
1. Criar um novo estoque.
1. Crie dois produtos:
   * Um produto somente com o estoque personalizado.
   * Um produto somente com o estoque padrão.
1. Adicionar esses produtos a uma categoria.
1. Vá para a [!UICONTROL visual Merchandising] grade (*[!UICONTROL Products in Category]*).

<u>Resultados Reais</u>:

No *[!UICONTROL All Store Views]* escopos, o produto com estoque personalizado não mostra nenhuma quantidade. É apenas quando a *[!UICONTROL Default Store View]* escopo for selecionado o estoque personalizado mostra a quantidade do produto.

<u>Resultados esperados</u>:

A grade mostra todas as informações de estoque se o escopo for *[!UICONTROL All Store Views]*.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.
