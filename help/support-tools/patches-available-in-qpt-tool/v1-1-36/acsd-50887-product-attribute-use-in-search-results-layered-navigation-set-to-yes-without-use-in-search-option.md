---
title: '"ACSD-50887: *[!UICONTROL Use in Search Results Layered Navigation]* defina como Sim sem *[!UICONTROL Use in Search]* opção'''
description: Aplique o patch ACSD-50887 para corrigir o problema do Adobe Commerce em que a propriedade de atributo do produto *[!UICONTROL Use in Search Results Layered Navigation]* pode ser definido como *Sim* sem o *[!UICONTROL Use in Search]* opção também sendo definida como *Sim*.
feature: Attributes, Products, Search, Storefront
role: Admin, Developer
exl-id: b597709b-7489-41a0-b1ff-d68d0def0b46
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 0%

---

# ACSD-50887: *[!UICONTROL Use in Search Results Layered Navigation]* definir como *Sim* sem o *[!UICONTROL Use in Search]* opção

O patch ACSD-50887 corrige o problema em que a propriedade do atributo do produto *[!UICONTROL Use in Search Results Layered Navigation]* pode ser definido como *Sim* sem o *[!UICONTROL Use in Search]* também está sendo definida como *Sim*. Este patch está disponível quando a variável [!DNL Quality Patches Tool (QPT)] O 1.1.36 está instalado. A ID do patch é ACSD-50887. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.0 - 2.4.6-p2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A propriedade do atributo de produto *[!UICONTROL Use in Search Results Layered Navigation]* pode ser definido como *Sim* sem o *[!UICONTROL Use in Search]* também está sendo definida como *Sim*.

Essas configurações foram projetadas para serem usadas juntas. Com o patch aplicado, quando a variável *[!UICONTROL Use in Search]* está definida como *Não*, o *[!UICONTROL Use in Search Results Layered Navigation]* está oculta para funcionar, como se também estivesse definida como *Não*.

<u>Etapas a serem reproduzidas</u>:

1. Em Admin, navegue até **[!UICONTROL Stores]** > **[!UICONTROL Attribute]** > **[!UICONTROL Product]** e crie um atributo com o tipo de multisseleção e defina o seguinte:

   * *[!UICONTROL Use in Search]= Não*
   * *[!UICONTROL Use in Layered Navigation]= (Qualquer opção)*
   * *[!UICONTROL Use in Search Results Layered Navigation]= Sim*
   * *Nome = Test_attribute*
   * *Opções*:
      * *Adesivo*
      * *Seletor*

1. Adicione o novo atributo ao conjunto de atributos padrão.
1. Crie dois produtos:

   1. Primeiro produto:
      * Nome = Adesivo
      * Definir Preço, QTD., Peso como 1
      * Test_attribute = opção de seleção *Adesivo*

   1. Segundo produto:
      * Nome = Seletor
      * Definir Preço, QTD., Peso como 1
      * Test_attribute = selecionar ambas as opções

1. Executar `catalogsearch_fulltext` reindexar:

   `bin/magento indexer:reindex catalogsearch_fulltext`

1. Pesquisar pela palavra *adesivo* na loja.

<u>Resultados esperados</u>:

Somente o produto *Adesivo* é retornado, porque [!DNL Elasticsearch] não indexará Test_attribute quando *[!UICONTROL Use in Search]* foi definido como *Não*.

<u>Resultados reais</u>:

Ambos os produtos são devolvidos.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.
