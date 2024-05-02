---
title: '[!DNL Elasticsearch] é exibido como o mecanismo de pesquisa apesar de [!DNL OpenSearch] instalação'
description: Este artigo fornece uma solução para o problema em que [!DNL Elasticsearch] ainda é exibido como mecanismo de pesquisa para o Adobe Commerce na nuvem, mesmo depois de instalar ou atualizar para [!DNL OpenSearch].
exl-id: cdd8a35d-da6f-46d3-b732-65626487c9bb
feature: Install
source-git-commit: 1a36e74807e6d32b0810416b6fb61aeca6f9be94
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 0%

---

# [!DNL Elasticsearch] é exibido como o mecanismo de pesquisa apesar de [!DNL OpenSearch] instalação

Este artigo fornece uma solução para o problema em que [!DNL Elasticsearch] ainda é exibido como mecanismo de pesquisa para o Adobe Commerce na nuvem, mesmo depois de instalar ou atualizar para [!DNL OpenSearch].

## Versões afetadas

Adobe Commerce na nuvem 2.4.3-p2 - 2.4.5-p6

>[!NOTE]
>
>[!DNL OpenSearch] O está disponível como um mecanismo de pesquisa a partir do Adobe Commerce 2.4.6.

## Problema

[!DNL Elasticsearch] ainda é exibido como mecanismo de pesquisa para o Adobe Commerce na nuvem, mesmo depois de instalar ou atualizar para [!DNL OpenSearch].

<u>Etapas a serem reproduzidas</u>:

1. Ir para **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog Search]**.
1. Verifique o mecanismo de pesquisa. Ele mostrará [!DNL Elasticsearch7].

## Causa

O Adobe Commerce está embutido em código para especificar [!DNL Elasticsearch7] como mecanismo de pesquisa.

## Solução

Para verificar se [!DNL OpenSearch] foi instalado, execute o seguinte comando:

**Método 1**:

* Execute o seguinte comando no servidor: `curl 127.0.0.1:9200`. Deve voltar [!DNL OpenSearch] com sua versão.

**Método 2**:

* Use o seguinte comando na CLI da Magento-cloud: `magento-cloud relationships -p <project_id>`. Depois de usar o comando, localize [!DNL OpenSearch].

## Leitura relacionada

[Configurar o serviço OpenSearch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/opensearch.html) no guia do Commerce na infraestrutura em nuvem.
