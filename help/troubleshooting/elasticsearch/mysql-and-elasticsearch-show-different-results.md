---
title: MySQL e Elasticsearch mostram resultados diferentes
description: Este artigo fornece um patch para o problema conhecido do Adobe Commerce na infraestrutura em nuvem 2.2.3 relacionado à obtenção de resultados de pesquisa diferentes para a mesma consulta de pesquisa com MySQL e Elasticsearch.
exl-id: 37a0164a-0237-4200-ab9c-e0dbad7e2062
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# MySQL e Elasticsearch mostram resultados diferentes

>[!WARNING]
>
> [O mecanismo de pesquisa do catálogo MySQL será removido no Adobe Commerce 2.4.0](/help/announcements/adobe-commerce-announcements/mysql-catalog-search-engine-will-be-removed-in-magento-2-4-0.md). Você deve ter o host de Elasticsearch configurado antes de instalar a versão 2.4.0. Consulte [Instalar e configurar o Elasticsearch](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/configuration-guide/search/overview-search) na documentação do desenvolvedor.

Este artigo fornece um patch para o problema conhecido do Adobe Commerce na infraestrutura em nuvem 2.2.3 relacionado à obtenção de resultados de pesquisa diferentes para a mesma consulta de pesquisa com MySQL e Elasticsearch.

## Problema:

Os resultados da pesquisa de catálogo com o mesmo conjunto de filtros diferem dependendo do mecanismo de pesquisa que está sendo usado, MySQL ou Elasticsearch.

<u>Etapas a serem reproduzidas</u>:

1. Instale e configure o Elasticsearch.
1. Na vitrine, selecione um dos filtros.
1. Anote o número de produtos correspondentes.
1. Configure a [Pesquisa do MySQL](/help/announcements/adobe-commerce-announcements/mysql-catalog-search-engine-will-be-removed-in-magento-2-4-0.md) padrão.
1. Na vitrine, selecione um dos filtros.
1. Anote o número de produtos correspondentes.

<u>Resultado esperado</u>:
O número de produtos correspondentes é o mesmo.

<u>Resultado real</u>:
O número de produtos correspondentes é diferente.

## Correção

Os patches estão anexados a este artigo. Para baixar um patch, role até o final do artigo e clique no nome de arquivo necessário ou clique nos seguintes links:

[Baixar MDVA-12312\_EE\_2.2.3\_COMPOSER\_v1.patch](assets/MDVA-12312_EE_2.2.3_COMPOSER_v1.patch.zip)

[Baixar MDVA-14172\_EE\_2.2.6\_COMPOSER\_v1.patch](assets/MDVA-14172_EE_2.2.6_COMPOSER_v1.patch.zip)

### Versões compatíveis do Adobe Commerce:

Os patches foram criados para:

* Adobe Commerce na infraestrutura em nuvem 2.2.3 (o arquivo `MDVA-12312_EE_2.2.3_COMPOSER_v1.patch`)
* Adobe Commerce na infraestrutura em nuvem 2.2.6 (o arquivo `MDVA-14172_EE_2.2.6_COMPOSER_v1.patch`)

O patch `MDVA-12312_EE_2.2.3_COMPOSER_v1.patch` também é compatível (mas pode não resolver o problema) com as seguintes versões e edições do Adobe Commerce:

* Adobe Commerce na infraestrutura em nuvem 2.2.4
* Adobe Commerce na infraestrutura em nuvem 2.2.5
* Adobe Commerce no local 2.2.3
* Adobe Commerce no local 2.2.4
* Adobe Commerce no local 2.2.5

O patch `MDVA-14172_EE_2.2.6_COMPOSER_v1.patch` também é compatível (mas pode não resolver o problema) com as seguintes versões e edições do Adobe Commerce:

* Adobe Commerce no local 2.2.6

## Como aplicar o patch

Consulte [Como aplicar um patch de compositor fornecido pelo Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) em nossa base de dados de conhecimento de suporte para obter instruções.

## Arquivos Anexados
