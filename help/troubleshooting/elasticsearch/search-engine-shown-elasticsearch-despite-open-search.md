---
title: '[!DNL Elasticsearch] é mostrado como o mecanismo de pesquisa apesar da instalação [!DNL OpenSearch] '
description: Este artigo fornece uma solução para o problema em que  [!DNL Elasticsearch]  ainda é exibido como mecanismo de pesquisa para Adobe Commerce na nuvem mesmo após a instalação ou atualização para  [!DNL OpenSearch].
exl-id: cdd8a35d-da6f-46d3-b732-65626487c9bb
feature: Install
source-git-commit: b3f68e43ce3c4fdea001db1d8ba2774900db7dba
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 0%

---

# [!DNL Elasticsearch] é mostrado como mecanismo de pesquisa apesar da instalação de [!DNL OpenSearch]

Este artigo fornece uma solução para o problema em que o [!DNL Elasticsearch] ainda é exibido como mecanismo de pesquisa para o Adobe Commerce na nuvem mesmo após a instalação ou atualização para o [!DNL OpenSearch].

## Versões afetadas

Adobe Commerce na nuvem 2.4.4 - 2.4.5-p11

>[!NOTE]
>
>[!DNL OpenSearch] está disponível como um mecanismo de pesquisa a partir do Adobe Commerce 2.4.6.

## Problema

[!DNL Elasticsearch] ainda é mostrado como o mecanismo de pesquisa do Adobe Commerce na nuvem mesmo após a instalação ou atualização para [!DNL OpenSearch].

<u>Etapas a serem reproduzidas</u>:

1. Vá para **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog Search]**.
1. Verifique o mecanismo de pesquisa. Ele mostrará [!DNL Elasticsearch7].

## Causa

[!DNL Elasticsearch7] está embutido em código no Adobe Commerce para ser o mecanismo de pesquisa usado nessas versões.

Isso não deve ser confundido com a versão instalada do serviço. Mesmo que não haja um módulo [!DNL Opensearch] incluído no código, a Adobe Commerce pode usar o serviço [!DNL Opensearch] subjacente.

## Solução

Para verificar se [!DNL OpenSearch] foi instalado, execute o seguinte comando:

**Método 1**:

* Execute o seguinte comando no servidor: `curl 127.0.0.1:9200`. Ele deve retornar [!DNL OpenSearch] com sua versão.

Exemplo:

```
$ curl 127.0.0.1:9200
{
  "name" : $clusterName,
  "cluster_name" : "opensearch_stg",
  "cluster_uuid" : $clusterUuid,
  "version" : {
    "distribution" : "opensearch",
    "number" : "1.2.4",
    "build_type" : "deb",
    "build_hash" : "44ccdbaed5fe5a8b02d99a611857a671b6dd909d",
    "build_date" : "2022-11-08T09:23:45.993372Z",
    "build_snapshot" : false,
    "lucene_version" : "8.10.1",
    "minimum_wire_compatibility_version" : "6.8.0",
    "minimum_index_compatibility_version" : "6.0.0-beta1"
  },
  "tagline" : "The OpenSearch Project: https://opensearch.org/"
}
```

**Método 2**:

* Use o seguinte comando na CLI da nuvem Magento: `magento-cloud relationships -p <project_id>`. Depois de usar o comando, localize [!DNL OpenSearch].

## Leitura relacionada

[Configure o serviço OpenSearch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/opensearch.html?lang=pt-BR) no guia Commerce na Infraestrutura na Nuvem.
