---
title: 'ACSD-53728: o indexador EAV do produto leva muito tempo para ser concluído'
description: Aplique o patch ACSD-53728 para corrigir o problema do Adobe Commerce em que o indexador EAV do produto está demorando muito para ser concluído.
feature: Products, Attributes
role: Admin, Developer
exl-id: 3e0601fb-7e2c-4f1b-8bd9-d2f09092db0e
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%

---

# ACSD-53728: o indexador EAV do produto leva muito tempo para ser concluído

O patch ACSD-53728 corrige o problema em que o indexador EAV do produto está demorando muito para ser concluído. Este patch está disponível quando o [!DNL Quality Patches Tool (QPT)] 1.1.37 está instalado. A ID do patch é ACSD-53728. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O indexador EAV do produto está demorando muito para ser concluído.

<u>Etapas a serem reproduzidas</u>:

1. Crie um grande número de produtos (por exemplo, cerca de 1300 produtos configuráveis).
1. Execute o reindexação de EAV do produto e meça o tempo:

   `run bin/magento index:reindex catalog_product_attribute`

<u>Resultados esperados</u>:

A reindexação leva um tempo razoável.

<u>Resultados reais</u>:

A reindexação leva muito tempo.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] versão: uma nova ferramenta para autoatender patches de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando o [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
