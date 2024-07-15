---
title: o robots.txt fornece o erro 404 Adobe Commerce na infraestrutura em nuvem
description: Este artigo fornece uma correção para quando o arquivo "robots.txt" lança um erro 404 no Adobe Commerce na infraestrutura em nuvem.
exl-id: 6f0b9f47-1901-4c43-88d8-fd992015d70f
feature: Cloud, Marketing Tools, Paas
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 0%

---

# o robots.txt fornece o erro 404 Adobe Commerce na infraestrutura em nuvem

Este artigo fornece uma correção para quando o arquivo `robots.txt` lança um erro 404 no Adobe Commerce na infraestrutura em nuvem.

## Produtos e versões afetados

Adobe Commerce na infraestrutura em nuvem (todas as versões)

## Problema

O arquivo `robots.txt` não está funcionando e gera uma exceção Nginx. O arquivo `robots.txt` é gerado dinamicamente &quot;em tempo real&quot;. O arquivo `robots.txt` não está acessível pela URL `/robots.txt` porque o Nginx tem uma regra de regravação que redireciona à força todas as solicitações `/robots.txt` para o arquivo `/media/robots.txt` que não existe.

## Causa

Isso normalmente acontece quando o Nginx não está configurado corretamente.

## Solução

A solução é desabilitar a regra Nginx que redireciona `/robots.txt` solicitações para o arquivo `/media/robots.txt`. Os comerciantes com autoatendimento habilitado podem fazer isso por conta própria, e os comerciantes sem autoatendimento habilitado precisam criar um tíquete de suporte.

Se você não tiver o autoatendimento habilitado (ou não tiver certeza se ele está habilitado), [envie um tíquete de Suporte Magento](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) solicitando a remoção da regra de redirecionamento Nginx das solicitações `/robots.txt` para `/media/robots.txt`.

Se o autoatendimento estiver habilitado, atualize as ECE-Tools para pelo menos 2002.0.12 e remova a regra de redirecionamento Nginx no arquivo `.magento.app.yaml`. Você pode consultar [Adicionar o mapa do site e os robôs do mecanismo de pesquisa](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/robots-sitemap.html) em nossa documentação do desenvolvedor para obter mais informações.

## Leitura relacionada

* [Como bloquear tráfego mal-intencionado para Magento Commerce Cloud no nível Fastly](/help/how-to/general/block-malicious-traffic-for-magento-commerce-on-fastly-level.md) em nossa base de dados de suporte.
* [Adicionar o mapa do site e os robôs do mecanismo de pesquisa](https://devdocs.magento.com/cloud/trouble/robots-sitemap.html) à documentação do desenvolvedor.
* [Robôs do Mecanismo de Pesquisa](https://experienceleague.adobe.com/docs/commerce-admin/marketing/seo/seo-overview.html#search-engine-robots) em nosso guia do usuário.
