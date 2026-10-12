---
title: Retornando para [!DNL Elasticsearch7] quando o mecanismo de pesquisa estiver definido como [!DNL Opensearch]
description: Este artigo fornece uma solução para o problema em que ocorre um erro *Fallback to [!DNL Elasticsearch7]* quando o mecanismo de pesquisa está definido como [!DNL OpenSearch] no Adobe Commerce.
feature: Search
role: Developer
exl-id: 965d2929-5cf0-4e0a-9eed-6a656daaa120
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
subfeature_v2:
  - id: a1d22079-48b9-5e69-9ee6-eb236068ef34
    internal-label: Search
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 0%
---
# Retornando para [!DNL Elasticsearch7] quando o mecanismo de pesquisa estiver definido como [!DNL Opensearch]

Este artigo fornece uma solução para o problema quando um erro *Falling back to[!DNL Elasticsearch7]* ocorre quando o mecanismo de pesquisa está definido como [!DNL OpenSearch] no Adobe Commerce.

## Versões afetadas

Adobe Commerce na infraestrutura em nuvem
2.4.4 - 2.4.4-p12
2.4.5 - 2.4.5-p11

>[!NOTE]
>
>O [!DNL OpenSearch] está disponível como um mecanismo de pesquisa a partir do Adobe Commerce 2.4.6, 2.4.5-p12, 2.4.4-p13.

## Problema

Você definiu o **mecanismo de pesquisa** como **[!DNL OpenSearch]**, mas este tipo de erro está presente no arquivo `var/log/support_report.log`:

`[2024-04-04T00:27:41.212916+00:00] report.ERROR: opensearch search engine doesn't exist. Falling back to elasticsearch7 [] []`

<u>Etapas a serem reproduzidas</u>:

1. Verifique se [!DNL OpenSearch] está instalado executando este comando: `curl 127.0.0.1:9200`<br>
Se ele indicar *1.2.4*, então [!DNL OpenSearch] já está instalado.
1. Vá para **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog Search]**.
1. Verifique o mecanismo de pesquisa. Ele mostrará [!DNL Elasticsearch7].

## Causa

Embora sua versão seja compatível com o [!DNL OpenSearch], o aplicativo somente reconhecerá/aceitará o [!DNL Elasticsearch7] como mecanismo de pesquisa.

A partir do Adobe Commerce versão 2.4.6, o aplicativo foi atualizado para permitir que [!DNL OpenSearch] seja selecionado como mecanismo de pesquisa.
Se você for para **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog Search]** em um ambiente que não seja de nuvem, poderá alterar essa opção, como mostrado na **Solução** abaixo.
(Observação: em um ambiente de nuvem, este campo não pode ser alterado porque o mecanismo de pesquisa está bloqueado no arquivo `app/etc/env.php`.)

## Solução

Atualize a variável `SEARCH_CONFIGURATION` no arquivo `.magento.env.yaml` e verifique se o **mecanismo de pesquisa** está definido como *[!DNL elasticsearch7]*.

## Leitura relacionada

[Configure o serviço OpenSearch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/opensearch.html?lang=pt-BR) no guia Commerce na Infraestrutura na Nuvem.
