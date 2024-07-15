---
title: "ACSD-56023: o conteúdo do widget não é atualizado na página do CMS"
description: Aplique o patch ACSD-56023 para corrigir o problema do Adobe Commerce em que o conteúdo do widget não é atualizado na página do CMS
feature: CMS
role: Admin, Developer
exl-id: 2ff33b1c-ae92-4c59-83d2-e252bf543bab
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# ACSD-56023: o conteúdo do widget não é atualizado na página do CMS

O patch ACSD-56023 corrige o problema em que o conteúdo do widget não é atualizado na página do CMS. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.44 está instalado. A ID do patch é ACSD-56023. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p5

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O conteúdo do widget não é atualizado na página do CMS.

<u>Etapas a serem reproduzidas</u>:

1. Crie alguns produtos.
1. Crie a nova página CMS e adicione o novo widget produtos ao conteúdo:

   ```
      {{widget type="Magento\Catalog\Block\Product\Widget\NewWidget" display_type="new_products" show_pager="1" products_per_page="5" products_count="10" template="product/widget/new/content/new_grid.phtml" page_var_name="pnetpm"}} 
   ```

1. Abra a página criada na loja. Armazene em cache.
1. No Administrador, abra **[!UICONTROL Catalog]** > **[!UICONTROL Products]**.
1. Escolha qualquer produto para edição e alterne **[!UICONTROL Set Product as New]** para *Sim*.
1. Acesse novamente a *página do CMS* criada na loja.

<u>Resultados esperados</u>:

A página contém o *widget Novos produtos* com os produtos.

<u>Resultados reais</u>:

A página não contém o *widget Novos produtos*, e os novos produtos não aparecem.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] versão: uma nova ferramenta para autoatender patches de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando o [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
