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

Este artigo fornece uma correção para quando a variável `robots.txt` o arquivo lança um erro 404 no Adobe Commerce na infraestrutura em nuvem.

## Produtos e versões afetados

Adobe Commerce na infraestrutura em nuvem (todas as versões)

## Problema

A variável `robots.txt` O arquivo não está funcionando e gera uma exceção do Nginx. A variável `robots.txt` o arquivo é gerado dinamicamente &quot;em tempo real&quot;. A variável `robots.txt` o arquivo não pode ser acessado pelo `/robots.txt` URL porque o Nginx tem uma regra de regravação que redireciona à força todos `/robots.txt` solicitações para o `/media/robots.txt` arquivo que não existe.

## Causa

Isso normalmente acontece quando o Nginx não está configurado corretamente.

## Solução

A solução é desativar a regra Nginx que redireciona `/robots.txt` solicitações para o `/media/robots.txt` arquivo. Os comerciantes com autoatendimento habilitado podem fazer isso por conta própria, e os comerciantes sem autoatendimento habilitado precisam criar um tíquete de suporte.

Se você não tiver o autoatendimento ativado (ou se não tiver certeza se ele está ativado), [enviar um tíquete de suporte do Magento](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) solicitando a remoção da regra de redirecionamento Nginx de `/robots.txt` solicitações para `/media/robots.txt`.

Se o autoatendimento estiver ativado, atualize as ECE-Tools para pelo menos 2002.0.12 e remova a regra de redirecionamento Nginx em `.magento.app.yaml` arquivo. Você pode consultar [Adicionar mapa do site e robôs de mecanismo de pesquisa](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/robots-sitemap.html) na documentação do desenvolvedor, para obter mais informações.

## Leitura relacionada

* [Como bloquear tráfego mal-intencionado para Magento Commerce Cloud no nível Fastly](/help/how-to/general/block-malicious-traffic-for-magento-commerce-on-fastly-level.md) em nossa base de conhecimento de suporte.
* [Adicionar mapa do site e robôs de mecanismo de pesquisa](https://devdocs.magento.com/cloud/trouble/robots-sitemap.html) na documentação do desenvolvedor.
* [Robôs do mecanismo de pesquisa](https://experienceleague.adobe.com/docs/commerce-admin/marketing/seo/seo-overview.html#search-engine-robots) em nosso guia do usuário.
