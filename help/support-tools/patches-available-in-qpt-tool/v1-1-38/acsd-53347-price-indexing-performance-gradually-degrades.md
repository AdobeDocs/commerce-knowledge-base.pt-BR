---
title: "ACSD-53347: o desempenho da indexação de preço degrada gradualmente as horas extras"
description: Aplique o patch ACSD-53347 para corrigir o problema do Adobe Commerce em que o desempenho diminui gradualmente ao reindexar preços para um catálogo de produtos grande.
feature: Price Indexer
role: Admin
exl-id: 28795673-54b0-4282-bd43-344401cbe140
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '404'
ht-degree: 0%

---

# ACSD-53347: o desempenho da indexação de preço diminui gradualmente ao longo do tempo

O patch ACSD-53347 corrige o problema em que o desempenho degrada gradualmente ao reindexar preços para um grande catálogo de produtos. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.38 está instalado. A ID do patch é ACSD-53347. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Ao reindexar preços para um catálogo de produtos grande, o desempenho das consultas executadas durante o processo de indexação diminui gradualmente.

<u>Etapas a serem reproduzidas</u>:

1. Crie um catálogo simples grande e atribua opções personalizadas a esses produtos (as opções personalizadas usam uma tabela temporária durante a indexação).
1. Crie pelo menos 200 grupos de clientes para aumentar a visibilidade do problema.
1. Crie dez ou mais sites e atribua todos os produtos a cada um deles.
1. Observe que os produtos importados são quase idênticos, diferindo somente pelo SKU e pelo nome.
1. Habilitar **[!UICONTROL DB Logging]**.
1. Execute o comando `bin/magento index:reindex catalog_product_price`.
1. Verifique se há *DELETE DE`catalog_product_index_price_opt_agr_temp`* em `db.log`.

<u>Resultados esperados</u>:

A execução de *consultas ao BD* é executada com eficiência.

<u>Resultados reais</u>:

O desempenho das *consultas de BD* em tabelas temporárias torna-se lento ao longo do tempo, portanto, a tabela de indexação de preços leva muito tempo para ser concluída.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] versão: uma nova ferramenta para autoatender patches de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando o [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
