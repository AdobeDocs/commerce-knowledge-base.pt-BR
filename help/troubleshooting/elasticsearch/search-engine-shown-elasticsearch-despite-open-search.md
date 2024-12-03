---
title: '[!DNL Elasticsearch] é mostrado como o mecanismo de pesquisa apesar da instalação [!DNL OpenSearch] '
description: Este artigo fornece uma solução para o problema em que  [!DNL Elasticsearch]  ainda é exibido como mecanismo de pesquisa para Adobe Commerce na nuvem mesmo após a instalação ou atualização para  [!DNL OpenSearch].
exl-id: cdd8a35d-da6f-46d3-b732-65626487c9bb
feature: Install
source-git-commit: 1f053f76ae56edc06bfe82e55210244c8ec4b8eb
workflow-type: tm+mt
source-wordcount: '223'
ht-degree: 0%

---

# [!DNL Elasticsearch] é mostrado como mecanismo de pesquisa apesar da instalação de [!DNL OpenSearch]

Este artigo fornece uma solução para o problema em que o [!DNL Elasticsearch] ainda é exibido como mecanismo de pesquisa para o Adobe Commerce na nuvem mesmo após a instalação ou atualização para o [!DNL OpenSearch].

## Versões afetadas

Adobe Commerce na nuvem 2.4.3-p2 - 2.4.5-p6

>[!NOTE]
>
>[!DNL OpenSearch] está disponível como um mecanismo de pesquisa a partir do Adobe Commerce 2.4.6.

## Problema

[!DNL Elasticsearch] ainda é mostrado como o mecanismo de pesquisa do Adobe Commerce na nuvem mesmo após a instalação ou atualização para [!DNL OpenSearch].

<u>Etapas a serem reproduzidas</u>:

1. Vá para **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog Search]**.
1. Verifique o mecanismo de pesquisa. Ele mostrará [!DNL Elasticsearch7].

## Causa

O Adobe Commerce está embutido em código para especificar [!DNL Elasticsearch7] como mecanismo de pesquisa.

Isso não deve ser confundido com a versão instalada do serviço. O aplicativo só reconhece [!DNL Elasticsearch7] como mecanismo de pesquisa, mas não [!DNL OpenSearch], mesmo que ele use o serviço [!DNL OpenSearch] subjacente como mecanismo no back-end.

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

* Use o seguinte comando na CLI Magento-cloud: `magento-cloud relationships -p <project_id>`. Depois de usar o comando, localize [!DNL OpenSearch].

## Leitura relacionada

[Configure o serviço OpenSearch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/opensearch.html) no guia Commerce na Infraestrutura na Nuvem.
