---
title: "ACSD-55100: [!DNL GraphQL] não retorna produtos acima de 10k em resultados de pesquisa"
description: Aplique o patch ACSD-55100 para corrigir o problema do Adobe Commerce em que a GraphQL não retorna produtos além de *10k* nos resultados da pesquisa.
feature: GraphQL, Products, Search
role: Admin, Developer
exl-id: 951e5cd4-9690-43df-9e51-deab73f9eb54
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '468'
ht-degree: 0%

---

# ACSD-55100: [!DNL GraphQL] não retorna produtos acima de 10.000 em resultados de pesquisa

O patch ACSD-55100 corrige o problema em que [!DNL GraphQL] não retorna produtos além de *10k* nos resultados da pesquisa. Este patch está disponível quando a variável [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.46 está instalado. A ID do patch é ACSD-55100. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

[!DNL GraphQL] não retorna produtos além de *10k* nos resultados da pesquisa.

<u>Pré-requisitos</u>:

No caso de **[!DNL OpenSearch]**, verifique se você está usando a versão mais recente disponível.

Para resolver o problema relatado, a funcionalidade Ponto no tempo é introduzida, que está disponível após **[!DNL OpenSearch]** 2.5.0 e exige a versão 2.2 do `opensearch-project/opensearch-php` pacote.

No entanto, existe um conflito com a `magento/magento-cloud-metapackage`, que especifica uma dependência no `opensearch-project/opensearch-php` pacote que deve ser anterior à versão 2.0.1.


Essa dependência impede a atualização do [opensearch-project/opensearch-php] para a versão mais recente 2.2.

Como resultado, o sistema encontra o seguinte erro e retorna resultados nulos para produtos que excedem *10.000*.

`Namespace [createPointInTime] not found in /vendor/opensearch-project/opensearch-php/src/OpenSearch/Client.php:135`

A dependência existente torna desafiador adicionar diretamente uma versão à `composer.json` arquivo e atualize o `opensearch-project/opensearch-php` pacote para a versão 2.2.

Para resolver o problema, inclua a seguinte linha no link principal `composer.json` arquivo no bloco obrigatório. Depois, reimplante para atualizar o pacote problemático para a versão mais recente.

`"opensearch-project/opensearch-php": "2.2.0 as 2.0.0",`

<u>Etapas a serem reproduzidas</u>:

1. Gerar o catálogo com *15 k* produtos.
1. Envie o [!DNL GraphQL]:

```
    query {
    products(
    filter: {
    # category_id:{eq:""}
    }
    , pageSize: 5, currentPage: 1

    ) {
    total_count
    page_info {
    current_page
    page_size
    total_pages
     }

     aggregations {

    attribute_code
    count
    label
    options {
    label
    value

    }
    }

    items {
    uid
    sku
    is_for_clearance
    categories {
    name
    breadcrumbs {
    category_name
    category_uid
    }
    display_mode
    description
    }
    }
    }
    }
```

<u>Resultados esperados</u>:

Total_count = *15 k*
Você poderá mostrar todos os produtos.

<u>Resultados reais</u>:

Total_count = *10k*
Não é possível obter mais nenhum produto para mostrar após a *10k* lote.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.
