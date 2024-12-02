---
title: 'ACSD-56415: desempenho de [!UICONTROL Partial Price Indexing] desacelerado devido à consulta "DELETE"'
description: Aplique o patch ACSD-56415 para corrigir o problema do Adobe Commerce em que o desempenho do [!UICONTROL Partial Price Indexing] é atrasado devido a uma consulta "DELETE" quando o banco de dados tem muitos dados de preço parciais para indexar.
feature: Catalog Service
role: Admin, Developer
exl-id: 0b099570-9f27-4ae2-9384-6b69ea50bd98
source-git-commit: 8b6bf1cdada7edb0cdb0bb3e90ed15ee8cebf77e
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# ACSD-56415: O desempenho de [!UICONTROL Partial Price Indexing] está lento devido à consulta `DELETE`

O patch ACSD-56415 corrige o problema em que o desempenho de [!UICONTROL Partial Price Indexing] é atrasado devido a uma consulta `DELETE` quando o banco de dados tem muito índice de dados de preço parcial. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.45 está instalado. A ID do patch é ACSD-56023. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6-p3

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O desempenho de [!UICONTROL Partial Price Indexing] está atrasado devido a uma consulta `DELETE` quando o banco de dados tem muito índice de dados de preço parcial.

<u>Etapas a serem reproduzidas</u>:

1. Crie *300000 produtos* e *10 sites* usando o perfil de desempenho grande.
1. Faça logon no Painel de administração.
1. Criar *10 grupos de clientes*.
1. Execute a consulta abaixo para adicionar produtos à tabela `_cl`:

   ``
    insert into catalog_product_price_cl (entity_id) select entity_id from catalog_product_entity
 ``

1. Execute o comando abaixo para acionar o processo de indexação de preço parcial:

   ``
    bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1
 ``

<u>Resultados esperados</u>:

O DELETE de consulta SQL `main_table` FROM `catalog_product_index_price` é executado rapidamente.

<u>Resultados reais</u>:

A DELETE de consulta SQL `main_table` FROM `catalog_product_index_price` é executada muito lentamente.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] versão: uma nova ferramenta para autoatender patches de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando o [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
