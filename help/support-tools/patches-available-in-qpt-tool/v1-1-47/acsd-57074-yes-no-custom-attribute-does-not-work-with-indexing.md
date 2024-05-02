---
title: "ACSD-57074: *Sim/Não* o atributo personalizado com o prefixo `price_*` no atributo `attribute_code` não funciona com a indexação"
description: Aplique o patch ACSD-57074 para corrigir o problema do Adobe Commerce em que o atributo personalizado *Sim/Não* com o prefixo `price_*` no atributo `attribute_code` não funciona com a indexação.
feature: Products, Categories, Catalog Management
role: Admin, Developer
exl-id: c620722f-a66d-4cae-9614-becec589a78c
source-git-commit: 4197f2a8f3d4775d3459b17bd92fa51a54ff9607
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# ACSD-57074: *Sim/Não* atributo personalizado com `price_*` prefixo em `attribute_code` o atributo não funciona com indexação

O patch ACSD-57074 corrige o problema em que o *Sim/Não* atributo personalizado com `price_*` prefixo no `attribute_code` O atributo não funciona com indexação. Este patch está disponível quando a variável [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.47 está instalado. A ID do patch é ACSD-57074. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6-p3

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6 - 2.4.6-p4

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A variável *Sim/Não* atributo personalizado com `price_*` prefixo no `attribute_code` O atributo não funciona com indexação.

<u>Etapas a serem reproduzidas</u>:

1. Crie um atributo de produto personalizado com as seguintes opções:
   * *[!UICONTROL Catalog Input Type]*: *Sim/Não*
   * *[!UICONTROL Scope]*: *StoreView*
   * *[!UICONTROL Use in Search]*: *Sim*
1. Atribua o atributo ao conjunto de atributos padrão.
1. Crie um produto com o atributo que criamos.
1. Atribua o produto que acabamos de criar a uma categoria.
1. Executar reindexação completa.

<u>Resultados esperados</u>:

O produto é exibido na categoria atribuída.

<u>Resultados reais</u>:

O produto não é exibido na página inicial da categoria.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.
