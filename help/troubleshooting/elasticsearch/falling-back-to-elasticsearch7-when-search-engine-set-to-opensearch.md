---
title: Retornando para [!DNL Elasticsearch7] quando o mecanismo de pesquisa estiver definido como [!DNL Opensearch]
description: Este artigo fornece uma solução para o problema quando um * Falling back to [!DNL Elasticsearch7]* error occurs when the search engine is set to [!DNL OpenSearch] no Adobe Commerce.
feature: Search
role: Developer
exl-id: 965d2929-5cf0-4e0a-9eed-6a656daaa120
source-git-commit: 6b8eecb3df0bb32344a5861a604a40402bb4d392
workflow-type: tm+mt
source-wordcount: '233'
ht-degree: 0%

---

# Retornando para [!DNL Elasticsearch7] quando o mecanismo de pesquisa estiver definido como [!DNL Opensearch]

Este artigo fornece uma solução para o problema quando uma *Retornando para[!DNL Elasticsearch7]* erro ocorre quando o mecanismo de pesquisa está definido como [!DNL OpenSearch] no Adobe Commerce.

## Versões afetadas

Adobe Commerce na infraestrutura em nuvem 2.4.4 - 2.4.5

>[!NOTE]
>
>[!DNL OpenSearch] O está disponível como um mecanismo de pesquisa a partir do Adobe Commerce 2.4.6.

## Problema

Você definiu o seu **mecanismo de pesquisa** para **[!DNL OpenSearch]**, mas veja esse tipo de erro no campo `var/log/support_report.log` arquivo:

```[2024-04-04T00:27:41.212916+00:00] report.ERROR: opensearch search engine doesn't exist. Falling back to elasticsearch7 [] []```

<u>Etapas a serem reproduzidas</u>:

1. Verifique se [!DNL OpenSearch] O é instalado executando este comando: `curl 127.0.0.1:9200`<br>
Se indicar *1.2.4*, depois [!DNL OpenSearch] já está instalado.
1. Ir para **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog Search]**.
1. Verifique o mecanismo de pesquisa. Ele mostrará [!DNL Elasticsearch7].

## Causa

Mesmo que sua versão seja compatível com [!DNL OpenSearch], o aplicativo só reconhecerá/aceitará [!DNL Elasticsearch7] como mecanismo de pesquisa.

A partir do Adobe Commerce versão 2.4.6, o aplicativo foi atualizado para permitir [!DNL OpenSearch] para ser selecionado como mecanismo de pesquisa.
Se você for a **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog Search]** em um ambiente que não seja de nuvem, é possível alterar essa opção, conforme mostrado na **Solução** abaixo.
(Observação: em um ambiente de nuvem, este campo não pode ser alterado porque o mecanismo de pesquisa está bloqueado no `app/etc/env.php` arquivo.)

## Solução

Atualize o `SEARCH_CONFIGURATION` na variável `.magento.env.yaml` e assegurar que o **mecanismo de pesquisa** está definida como *[!DNL elasticsearch7]*.

## Leitura relacionada

[Configurar o serviço OpenSearch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/opensearch.html) no guia do Commerce na infraestrutura em nuvem.
