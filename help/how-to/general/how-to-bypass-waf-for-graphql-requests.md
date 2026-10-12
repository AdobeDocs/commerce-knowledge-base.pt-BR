---
title: Como ignorar as solicitações do WAF para GraphQL
description: Este artigo explica como ignorar o WAF nas solicitações do GraphQL.
feature: GraphQL
exl-id: 3a0f2c22-f976-4596-b6a9-4634be1ea4c3
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: c32adafa-ed01-4b31-997e-2413013911b0
    internal-label: Integrations
subfeature_v2:
  - id: e396cff5-f586-484c-89f0-7f1da3308f92
    internal-label: GraphQL
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '158'
ht-degree: 0%
---
# Como ignorar as solicitações do WAF para GraphQL

Este artigo explica como ignorar solicitações do WAF for GraphQL quando o WAF [!DNL Fastly] estiver bloqueando suas solicitações do GraphQL.

## Produtos e versões afetados

Adobe Commerce na infraestrutura em nuvem (todas as versões)

## Causa

Devido à natureza inerente das solicitações do GraphQL, pode haver muitos caracteres repetidos que acionam o bloqueio falso positivo das solicitações pelo WAF [!DNL Fastly].

## Solução

1. Ignore a WAF para essas solicitações adicionando um trecho personalizado por meio do módulo Magento [!DNL Fastly]:

   tipo: recv
   prioridade: 15
   conteúdo:

   ```
   if( req.url.path ~ "^/graphql" ) {
       set req.http.bypasswaf = "1";
   }
   ```

1. Clique em **[!UICONTROL Upload VCL to Fastly]**.

## Leitura relacionada

* [Firewall do Aplicativo Web (WAF)](https://experienceleague.adobe.com/pt-br/docs/commerce-cloud-service/user-guide/cdn/fastly-waf-service) no guia Commerce on Cloud Infrastructure.
* [Introdução ao VCL personalizado](https://experienceleague.adobe.com/pt-br/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-custom-snippets) no guia do Commerce on Cloud Infrastructure.
