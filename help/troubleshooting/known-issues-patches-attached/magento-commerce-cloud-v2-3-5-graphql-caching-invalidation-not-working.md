---
title: A invalidação do armazenamento em cache do GraphQL do Adobe Commerce na infraestrutura em nuvem v2.3.5 não está funcionando
description: Este artigo fornece uma correção para o problema em que a solicitação do GraphQL "GET" retorna informações desatualizadas se o cliente alterar as informações do produto.
exl-id: 10ae52bd-e71a-42e3-9600-7a9713903815
feature: GraphQL, Cache, Categories, Cloud, Paas
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 0%

---

# A invalidação do armazenamento em cache do GraphQL do Adobe Commerce na infraestrutura em nuvem v2.3.5 não está funcionando

Este artigo fornece uma correção para o problema em que a solicitação do GraphQL `GET` retorna informações desatualizadas se o cliente alterar as informações do produto.

## Produtos e versões afetados

Adobe Commerce na infraestrutura em nuvem v2.3.5.

## Problema

As solicitações do GraphQL são armazenadas em cache pelo Fastly e a versão em cache é recuperada para cada solicitação subsequente do Fastly. Quando um produto é salvo novamente no back-end do Adobe Commerce, o cache do Fastly deve invalidar quando um produto é atualizado. No entanto, ela permanece válida.

<u>Etapas a serem reproduzidas</u>:

1. Acione a seguinte solicitação do GraphQL para obter produtos para determinada categoria, como:
   <pre><magento2-server>
    </pre>
1. Salve novamente um dos produtos recuperados pela solicitação acima no Administrador do Commerce.
1. Acione a solicitação novamente.

<u>Resultados esperados</u>:

O cabeçalho `X-Cache` contém `MISS`.

<u>Resultados reais</u>:

O cabeçalho `X-Cache` contém `HIT`, o que significa que a resposta está armazenada em cache.

## Solução

Desative o cache de produto do GraphQL com o patch fornecido neste artigo.

## Correção

O patch está anexado a este artigo. Para baixá-lo, role para baixo até o final do artigo e clique no nome do arquivo ou clique no link a seguir:

[MDVA-28559\_EE\_2.3.5-p1\_COMPOSER\_v1.patch](assets/MDVA-28559_EE_2.3.5-p1_v1.composer.patch.zip)

### Versões compatíveis do Adobe Commerce:

A correção foi criada para:

* Adobe Commerce na infraestrutura em nuvem v2.3.5

O patch também é compatível (mas pode não resolver o problema) com as seguintes versões e edições do Adobe Commerce:

* Adobe Commerce na infraestrutura em nuvem v2.4.0
* Adobe Commerce no local v2.4.0
* Adobe Commerce na infraestrutura em nuvem v2.3.5-p2
* Adobe Commerce no local v2.3.5-p2
* Adobe Commerce na infraestrutura em nuvem v2.3.5-p1
* Adobe Commerce no local v2.3.5-p1
* Adobe Commerce no local v2.3.5
* Adobe Commerce na infraestrutura em nuvem v2.3.4-p2
* Adobe Commerce no local v2.3.4-p2
* Adobe Commerce na infraestrutura em nuvem v2.3.4
* Adobe Commerce no local v2.3.4
* Adobe Commerce no local v2.3.3-p1
* Adobe Commerce no local v2.3.3

## Como aplicar o patch

Consulte [Como aplicar um patch de compositor fornecido pelo Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) para obter instruções sobre como aplicar um patch de compositor.

## Arquivos anexados
