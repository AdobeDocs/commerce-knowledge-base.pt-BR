---
title: "ACSD-49179: o relatório de pedidos mostra valores incorretos para armazenamentos diferentes."
description: Aplique o patch ACSD-49179 para corrigir o problema do Adobe Commerce em que o relatório de pedidos mostra valores incorretos no caso de moedas diferentes para lojas diferentes.
exl-id: 01e4cd2d-6c33-4cf5-bf31-bbc34eaaed1a
feature: Admin Workspace, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 0%

---

# ACSD-49179: O relatório de pedidos mostra valores incorretos para armazenamentos diferentes

O patch ACSD-49179 corrige o problema em que o relatório de pedidos mostra valores incorretos no caso de moedas diferentes para lojas diferentes. Este patch está disponível quando a variável [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.28 está instalado. A ID do patch é ACSD-49179. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3-p3

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2 - 2.4.6

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O relatório de pedidos mostra valores incorretos no caso de moedas diferentes para lojas diferentes.

<u>Etapas a serem reproduzidas</u>:

1. Ir para **[!UICONTROL Stores]** > **[!UICONTROL Config]** > **[!UICONTROL Catalog]** > **[!UICONTROL Price]** e defina [!UICONTROL Catalog Price Scope] = [!UICONTROL Website].
1. Crie um site adicional, loja e visualização de loja.
1. Ir para **[!UICONTROL Stores]** > **[!UICONTROL Config]** > **[!UICONTROL General]** > **[!UICONTROL Currency Setup]** > **[!UICONTROL Currency Options]** e defina:
   * Configuração padrão:
      * Moeda de base: USD
      * Moeda de Exibição Padrão: USD
      * Moedas permitidas: EUR, USD e THB (Baht tailandês)
   * Site principal:
      * Moeda de base: EUR
      * Moeda de Exibição Padrão: EUR
      * Moedas permitidas: EUR
   * Novo site adicional:
      * Moeda de base: THB (Baht tailandês)
      * Moeda de exibição padrão: THB (Baht tailandês)
      * Moedas permitidas: THB (Baht tailandês)
1. Ir para **[!UICONTROL Stores]** > **[!UICONTROL Currency]** > **[!UICONTROL Currency Rates]** e defina as taxas de conversão vazias para o THB (defina as taxas como 1,0000).
1. Crie um produto, atribua-o aos dois sites e faça um pedido com esse produto no site adicional criado anteriormente.
1. Certifique-se de que o pedido esteja em *Processando* status (faturar).
1. No back-end, acesse **[!UICONTROL Reports]** > **[!UICONTROL Sales]** > **[!UICONTROL Orders]**.
1. Clique no link **[!UICONTROL Yellow]** aviso para atualizar as estatísticas.
1. Defina o escopo do relatório no site adicional criado anteriormente e defina o filtro da seguinte maneira:
   * [!UICONTROL Date Used]: [!UICONTROL Created]
   * [!UICONTROL Period]: [!UICONTROL Day]
   * [!UICONTROL From and To]: o mesmo dia em que o pedido de teste foi feito
   * [!UICONTROL Order Status]: [!UICONTROL Any]
   * [!UICONTROL Empty rows]: [!UICONTROL No]
   * [!UICONTROL Show Actual Values]: [!UICONTROL No]

<u>Resultados esperados</u>:

Total de vendas mostra o valor correto convertido na moeda do site.

<u>Resultados reais</u>:

O total é zero.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.
