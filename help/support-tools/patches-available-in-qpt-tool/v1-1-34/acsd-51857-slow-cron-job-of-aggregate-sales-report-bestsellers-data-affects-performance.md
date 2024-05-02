---
title: '"ACSD-51857: trabalho cron lento de "aggregate_sales_report_bestsellers_data" afeta o desempenho"'
description: Aplique o patch ACSD-51857 para corrigir o problema do Adobe Commerce em que o trabalho lento do cron "aggregate_sales_report_bestsellers_data" afeta grandes tabelas de banco de dados "sales_order" e "sales_order_item".
exl-id: 444ab283-c98b-46b3-a492-706f0ce34a27
source-git-commit: a33364531d2efd572cd1b1847dd45e0f427af03b
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# ACSD-51857: trabalho de cron lento de `aggregate_sales_report_bestsellers_data` afeta o desempenho

O patch ACSD-51857 corrige o problema em que o trabalho cron lento `aggregate_sales_report_bestsellers_data` afeta grandes `sales_order` e `sales_order_item` tabelas de banco de dados. Este patch está disponível quando a variável [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.34 está instalado. A ID do patch é ACSD-51857. Observe que o problema foi corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.0 - 2.4.6-p2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Desempenho do trabalho do Cron de `aggregate_sales_report_bestsellers_data` está lento em `sales_order` e `sales_order_item` tabelas de banco de dados.

Para resolver isso, a consulta de dados principais que captura dados para o relatório foi regravada em um formulário mais eficiente. Agora, ele usa uma subconsulta para determinar o subconjunto de dados.

Para que a subconsulta funcione o mais rápido possível, um novo índice foi adicionado para o `sales_order` tabela de banco de dados: `SALES_ORDER_STORE_STATE_CREATED` baseado em `store_id`, `state`, e `created_at` colunas.

<u>Pré-requisitos</u>

Garanta um grande número de pedidos diariamente.

<u>Etapas a serem reproduzidas</u>

1. Execute o `aggregate_sales_report_bestsellers_data` trabalho cron.
1. Verifique os dados a serem exibidos no painel do Administrador, sob o **[!UICONTROL Bestsellers]** guia.

<u>Resultados esperados</u>:

*[!UICONTROL Quantity per source]* no **[!UICONTROL Configuration]** A guia não deve estar vazia.

<u>Resultados reais</u>:

*[!UICONTROL Quantity per source]* no **[!UICONTROL Configuration]** está vazia.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.
