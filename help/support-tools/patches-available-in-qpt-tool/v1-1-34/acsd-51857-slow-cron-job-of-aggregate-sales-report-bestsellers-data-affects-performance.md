---
title: '"ACSD-51857: trabalho cron lento de "aggregate_sales_report_bestsellers_data" afeta o desempenho"'
description: Aplique o patch ACSD-51857 para corrigir o problema do Adobe Commerce em que o trabalho lento do cron "aggregate_sales_report_bestsellers_data" afeta grandes tabelas de banco de dados "sales_order" e "sales_order_item".
exl-id: 444ab283-c98b-46b3-a492-706f0ce34a27
source-git-commit: a33364531d2efd572cd1b1847dd45e0f427af03b
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# ACSD-51857: O trabalho cron lento de `aggregate_sales_report_bestsellers_data` afeta o desempenho

O patch ACSD-51857 corrige o problema em que o trabalho lento do cron `aggregate_sales_report_bestsellers_data` afeta tabelas de banco de dados `sales_order` e `sales_order_item` grandes. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.34 está instalado. A ID do patch é ACSD-51857. Observe que o problema foi corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.0 - 2.4.6-p2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O desempenho do trabalho do Cron de `aggregate_sales_report_bestsellers_data` está lento nas tabelas de banco de dados de `sales_order` e `sales_order_item`.

Para resolver isso, a consulta de dados principais que captura dados para o relatório foi regravada em um formulário mais eficiente. Agora, ele usa uma subconsulta para determinar o subconjunto de dados.

Para que a subconsulta funcione o mais rápido possível, um novo índice foi adicionado para a tabela de banco de dados `sales_order`: `SALES_ORDER_STORE_STATE_CREATED` com base nas colunas `store_id`, `state` e `created_at`.

<u>Pré-requisitos</u>

Garanta um grande número de pedidos diariamente.

<u>Etapas a serem reproduzidas</u>

1. Execute o trabalho cron `aggregate_sales_report_bestsellers_data`.
1. Verifique os dados a serem exibidos no painel de Administração, na guia **[!UICONTROL Bestsellers]**.

<u>Resultados esperados</u>:

*[!UICONTROL Quantity per source]* na guia **[!UICONTROL Configuration]** não deve estar vazio.

<u>Resultados reais</u>:

*[!UICONTROL Quantity per source]* na guia **[!UICONTROL Configuration]** está vazio.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] versão: uma nova ferramenta para autoatender patches de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando o [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
