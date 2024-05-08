---
title: Como ignorar o WAF para solicitações do GraphQL
description: Este artigo explica como ignorar o WAF nas solicitações do GraphQL.
feature: GraphQL
source-git-commit: c35d4ba82fbe1657756e160a73fd575c736b4e1c
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 0%

---

# Como ignorar o WAF para solicitações do GraphQL

Este artigo explica como ignorar o WAF em solicitações do GraphQL quando o [!DNL Fastly] O WAF está bloqueando as solicitações do GraphQL.

## Produtos e versões afetados

Adobe Commerce na infraestrutura em nuvem (todas as versões)

## Causa

Devido à natureza inerente das solicitações do GraphQL, pode haver muitos caracteres repetidos que acionam o bloqueio falso positivo das solicitações pelo [!DNL Fastly] WAF.

## Solução

1. Ignore o WAF dessas solicitações adicionando um trecho personalizado por meio da [!DNL Fastly] Módulo Magento:

   tipo: recv prioridade: 15 conteúdo:

   ```
   if( req.url.path ~ "^/graphql" ) {
       set req.http.bypasswaf = "1";
   }
   ```

1. Clique em **[!UICONTROL Upload VCL to Fastly]**.

## Leitura relacionada

* [Firewall de Aplicativo Web (WAF)](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/fastly-waf-service) no guia do Commerce na infraestrutura em nuvem.
* [Introdução ao VCL personalizado](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-custom-snippets) no guia do Commerce na infraestrutura em nuvem.

