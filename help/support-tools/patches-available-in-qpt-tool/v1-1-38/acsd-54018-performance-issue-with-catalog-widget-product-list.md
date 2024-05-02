---
title: "ACSD-54018: problema de desempenho com a lista de produtos do widget de catálogo"
description: Aplique o patch ACSD-54018 para corrigir o problema do Adobe Commerce em que a página é carregada lentamente ao adicionar uma lista de produtos widget de catálogo com condição e tipo de atributo booleano.
feature: Attributes, Catalog Management, Page Builder, Page Content, Storefront
role: Admin, Developer
exl-id: 9f20484d-58c7-49d8-87df-1eeb84bee6fe
source-git-commit: dccb8dde1666fa0c72c7c94cd94c82daddaadc54
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 0%

---

# ACSD-54018: problema de desempenho com a lista de produtos do widget de catálogo

O patch ACSD-54018 corrige o problema em que a página é carregada lentamente ao adicionar uma lista de produtos widget de catálogo com condição e tipo de atributo booleano. Este patch está disponível quando a variável [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.38 está instalado. A ID do patch é ACSD-54018. Observe que o problema foi corrigido no Adobe Commerce 2.4.6.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.7 - 2.4.5-p4

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A página carrega lentamente ao adicionar uma lista de produtos widget de catálogo com condição e tipo de atributo booleano.

<u>Etapas a serem reproduzidas</u>:

1. Gerar 100k produtos.
1. Crie um atributo bool com o escopo definido como [!UICONTROL Store View].
1. Atribuir atributo a todos os conjuntos de atributos.
   * Atribuir o valor do atributo *Sim* a todos os produtos.
1. Agora vá para **[!UICONTROL Catalog]** > **[!UICONTROL Products]** e selecione todos os produtos 100k.
   * Escolher **[!UICONTROL Actions]** > **[!UICONTROL Update Attribute]**.
   * Definir o atributo bool como *Sim* e salve-o.
   * Se você tiver feito logout nesta etapa, verifique a *Notas*.
1. Vá para a CLI e execute `php bin/magento queue:con:start product_action_attribute.update`.
   * Verifique se os atributos de todos os produtos foram atualizados.
1. Agora vá para **[!UICONTROL Content]** > **[!UICONTROL Pages]** e criar uma nova página.
1. Abertura **[!UICONTROL Page Builder]** > **[!UICONTROL Add row]** > **[!UICONTROL Add Content]** > **[!UICONTROL Products]**.
1. Escolher *[!UICONTROL Select Products By]* = *[!UICONTROL Condition]*.
1. Definir a condição *[!UICONTROL Created attribute]* para *[!UICONTROL Yes]* e salve-o.
1. Vá para o front-end e abra a página criada.
1. Desative o cache de página inteira e bloqueie o cache html.
1. Verifique a velocidade de carregamento da página.
1. Recarregue a página algumas vezes e calcule o tempo médio de carregamento.

<u>Resultados esperados</u>:

A página carrega rapidamente.

<u>Resultados reais</u>:

O carregamento da página leva de 5 a 10 segundos.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.
