---
title: Reduza "oauth_tokens" expirado antes da atualização 2.4.6
description: Este artigo fornece uma solução para o problema em que você vê um grande número de "oauth_tokens" na tabela "oauth_token", o que pode causar um grande atraso na atualização para a versão 2.4.6. Recomenda-se reduzir a tabela "oauth_token" usando CleanExpiredTokens.php.
feature: Variables, Upgrade
role: Developer
exl-id: 92d1d15a-04da-4ba4-b6b8-5c491af9c4c1
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '258'
ht-degree: 0%

---

# Reduza o(s) `oauth_tokens` expirado(s) antes da atualização para 2.4.6

Este artigo fornece uma solução para o problema em que você vê um grande número de `oauth_tokens` na tabela `oauth_token`, o que pode causar um grande atraso na atualização para a versão 2.4.6. É recomendável reduzir a tabela `oauth_token` usando o trabalho [`CleanExpiredTokens.php`](https://github.com/magento/magento2/blob/2.4.5-p2/app/code/Magento/Integration/Cron/CleanExpiredTokens.php) [!DNL cron] para excluir os tokens expirados.

## Produtos e versões afetados

* Adobe Commerce 2.4.0 - 2.4.6, todos os métodos de implantação

## Problema

Se houver um grande número de `oauth_tokens` na tabela `oauth_token`, isso poderá causar um grande atraso na atualização para a versão 2.4.6.

O processo de atualização inclui a criptografia desses tokens para uma camada extra de segurança, e só é feito 100 registros de cada vez. Isso pode levar várias horas se houver um grande número de tokens.

Reduzir um grande número de `oauth_tokens` na tabela `oauth_token` pode evitar um grande atraso na atualização para a versão 2.4.6.

## Solução

Antes de iniciar uma atualização, verifique se o trabalho [`CleanExpiredTokens.php`](https://github.com/magento/magento2/blob/2.4.5-p2/app/code/Magento/Integration/Cron/CleanExpiredTokens.php) [!DNL cron] está em execução. Ele reduz o tamanho da tabela `oauth_token` ao excluir os `oauth_tokens` tokens expirados, e já deve estar habilitado por padrão.

Para acionar manualmente o trabalho [`CleanExpiredTokens.php`](https://github.com/magento/magento2/blob/2.4.5-p2/app/code/Magento/Integration/Cron/CleanExpiredTokens.php) [!DNL cron], execute:
```bin/magento cron:run --group=default```

## Leitura relacionada

* [Serviços > [!DNL OAuth]](https://experienceleague.adobe.com/docs/commerce-admin/config/services/oauth.html?lang=pt-BR) no guia de Referência de Configuração do Commerce
* [Guia de Autenticação](https://developer.adobe.com/developer-console/docs/guides/authentication/) no guia do Adobe Developer
* [Práticas recomendadas para modificar tabelas de banco de dados](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) no Manual de implementação do Commerce
