---
title: '"ACSD-53750: erro "Tubulação quebrada ou conexão fechada" durante reindexação de catalog_product_price de multithread"'
description: Aplique o patch ACSD-53750 para corrigir o problema do Adobe Commerce em que um erro *Pipe quebrado ou conexão fechada* ocorre durante a reindexação de vários threads catalog_product_price.
feature: Products
role: Admin, Developer
exl-id: afb30384-74e7-4857-9aff-8e99f5abc309
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 0%

---

# ACSD-53750: *Pipe quebrado ou conexão fechada* erro durante multithread `catalog_product_price` reindexar

O patch ACSD-53750 corrige o problema em que um *Pipe quebrado ou conexão fechada* o erro ocorre durante multithread `catalog_product_price` reindexar. Este patch está disponível quando a variável [!DNL Quality Patches Tool (QPT)] O 1.1.37 está instalado. A ID do patch é ACSD-53750. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.6-p2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

*Pipe quebrado ou conexão fechada* o erro ocorre durante multithread `catalog_product_price` reindexar.

<u>Etapas a serem reproduzidas</u>:

1. Configurar RabbitMq.
1. Gerar dados de amostra usando o anexo `small.xml` arquivo.
1. Ir para **[!UICONTROL Stores]** > **[!UICONTROL Config]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Inventory Indexer Setting]** e defina **[!UICONTROL Stock/Source reindex strategy]** = **[!UICONTROL Asynchronous]**.
1. Defina o modo de dimensão para índices que suportam isso. Por exemplo, `catalog_product_price_website_and_customer_group` ou `customer_group`.

   ```
   bin/magento indexer:set-dimensions-mode catalog_product_price customer_group
   ```

1. Executar redefinição de indexadores para `catalog_product_price`.

   ```
   bin/magento indexer:reset catalog_product_price
   ```

1. Execute o indexador para o indexador de redefinição usando vários threads.

   ```
   MAGE_INDEXER_THREADS_COUNT=10 bin/magento indexer:reindex catalog_product_price
   ```

<u>Resultados esperados</u>:

Nenhum erro ocorre.

<u>Resultados reais</u>:

O seguinte erro é causado por uma conexão AMQP: *Pipe quebrado ou conexão fechada*.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.
