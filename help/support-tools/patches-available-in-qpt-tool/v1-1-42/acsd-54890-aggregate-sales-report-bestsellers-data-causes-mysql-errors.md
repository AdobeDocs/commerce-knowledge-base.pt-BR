---
title: 'ACSD-54890: "aggregate_sales_report_bestsellers_data" causa  [!DNL MySQL] erros'
description: Aplique o patch ACSD-54890 para corrigir o problema do Adobe Commerce em que "aggregate_sales_report_bestsellers_data" causa  [!DNL MySQL] erros devido a &grave;/tmpdisk&grave; estar sem espaço.
feature: Attributes
role: Admin, Developer
exl-id: 21a675dc-0750-4dc6-8cce-33e301f601bd
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '309'
ht-degree: 0%

---

# ACSD-54890: `aggregate_sales_report_bestsellers_data` causa erros do MySQL

O patch ACSD-54890 corrige o problema em que `aggregate_sales_report_bestsellers_data` causa erros [!DNL MySQL] devido a `/tmpdisk` ficar sem espaço. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.42 está instalado. A ID do patch é ACSD-54890. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O `aggregate_sales_report_bestsellers_data` causa **[!DNL MySQL]** erros porque `/tmpdisk` está sem espaço.

<u>Etapas a serem reproduzidas</u>:

Execute o trabalho cron `aggregate_sales_report_bestsellers_data` quando a tabela `sales_bestsellers_aggregated_daily` tiver uma quantidade enorme de registros, como dezenas de milhões de registros.

<u>Resultados esperados</u>:

Nenhum erro ocorre.

<u>Resultados reais</u>:

Ocorre o seguinte erro:
`report.ERROR: Cron Job aggregate_sales_report_bestsellers_data has an error: SQLSTATE[HY000]: General error: 3 Error writing file '/tmp/#sql/fd=72' (Errcode: 28 "No space left on device")`

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] versão: uma nova ferramenta para autoatender patches de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando o [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
