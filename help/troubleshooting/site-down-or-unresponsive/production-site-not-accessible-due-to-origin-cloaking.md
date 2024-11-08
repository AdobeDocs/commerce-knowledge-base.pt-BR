---
title: Site não acessível devido ao encobrimento de origem
description: Este artigo fornece uma solução para quando a loja e/ou o administrador da infraestrutura em nuvem ou preparo do Adobe Commerce no site de produção não estiverem acessíveis.
exl-id: 4412d744-3066-4f78-bc45-8149614ce455
feature: Products
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '216'
ht-degree: 0%

---

# Site não acessível devido ao encobrimento de origem

Este artigo fornece uma solução para quando a loja e/ou o administrador da infraestrutura em nuvem ou preparo do Adobe Commerce no site de produção não estiverem acessíveis.

## Produtos e versões afetados

* Adobe Commerce na infraestrutura em nuvem 2.3.x, 2.4.x

## Problema

https:&#x200B;//mydomain.com.c.&lt;projectid>.magento.cloud/ não está mais acessível.

<u>Etapas a serem reproduzidas:</u>

1. Faça logon no projeto.
1. Clique em **Acessar projeto** para obter uma lista de URLs e SSH.

<u>Resultados reais:</u>

Falha ao carregar a página com o seguinte erro:

*NET::ERR\_CERT\_INVALID* *Alerta TLS, certificado inválido (554):*

<u>Resultados esperados:</u>

A página foi carregada com sucesso.

## Causa

O Camuflagem de origem foi ativado, portanto, a origem não é mais acessível diretamente.

O cloaking de origem é um recurso de segurança que permite que o Adobe Commerce bloqueie qualquer tráfego que não seja do Fastly na infraestrutura da nuvem (origem) para evitar ataques de DDoS.

## Solução

* Se o site na nuvem estiver ativo, alterne para https://mydomain.com/.
* Se você tiver um site ativo (não nuvem), usando o domínio https://mydomain.com/, configure um subdomínio `mcprod.mydomain.com` e atualize sua **URL Base** para *https://mcprod.mydomain.com* e depois [aponte o DNS para Fastly](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration#update-dns-configuration-with-development-settings).

## Leitura relacionada

[Perguntas frequentes sobre a habilitação do Fastly origin cloaking](/help/faq/general/fastly-origin-cloaking-enablement-faq.md) em nossa base de dados de conhecimento de suporte.
