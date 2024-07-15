---
title: Como ignorar o WAF para solicitações do GraphQL
description: Este artigo explica como ignorar o WAF nas solicitações do GraphQL.
feature: GraphQL
exl-id: 3a0f2c22-f976-4596-b6a9-4634be1ea4c3
source-git-commit: 2bec86818336a9ef4d8316e257a0ca4256cdd93c
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 0%

---

# Como ignorar o WAF para solicitações do GraphQL

Este artigo explica como ignorar o WAF em solicitações do GraphQL quando o WAF [!DNL Fastly] estiver bloqueando solicitações do GraphQL.

## Produtos e versões afetados

Adobe Commerce na infraestrutura em nuvem (todas as versões)

## Causa

Devido à natureza inerente das solicitações do GraphQL, pode haver muitos caracteres repetidos que acionam o bloqueio falso positivo das solicitações pelo WAF [!DNL Fastly].

## Solução

1. Ignore o WAF dessas solicitações adicionando um trecho personalizado por meio do módulo de Magento [!DNL Fastly]:

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

* [Web Application Firewall (WAF)](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/fastly-waf-service) no guia Commerce on Cloud Infrastructure.
* [Introdução ao VCL personalizado](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-custom-snippets) no guia do Commerce on Cloud Infrastructure.
