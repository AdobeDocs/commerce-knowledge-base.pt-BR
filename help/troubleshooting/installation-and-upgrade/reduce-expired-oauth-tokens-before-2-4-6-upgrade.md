---
title: Reduza "oauth_tokens" expirado antes da atualização 2.4.6
description: Este artigo fornece uma solução para o problema em que você vê um grande número de "oauth_tokens" na tabela "oauth_token", o que pode causar um grande atraso na atualização para a versão 2.4.6. Recomenda-se reduzir a tabela "oauth_token" usando CleanExpiredTokens.php.
feature: Variables, Upgrade
role: Developer
exl-id: 92d1d15a-04da-4ba4-b6b8-5c491af9c4c1
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '246'
ht-degree: 0%

---

# Redução expirada `oauth_tokens` antes da atualização do 2.4.6

Este artigo fornece uma solução para o problema em que você vê um grande número de `oauth_tokens` no seu `oauth_token` tabela, que pode causar um grande atraso na atualização para a versão 2.4.6. É recomendável reduzir o `oauth_token` tabela usando o [`CleanExpiredTokens.php`](https://github.com/magento/magento2/blob/2.4.5-p2/app/code/Magento/Integration/Cron/CleanExpiredTokens.php) [!DNL cron] tarefa para excluir os tokens expirados.

## Produtos e versões afetados

* Adobe Commerce 2.4.0 - 2.4.6, todos os métodos de implantação

## Problema

Se houver um grande número de `oauth_tokens` no seu `oauth_token` tabela, que pode causar um grande atraso na atualização para a versão 2.4.6.

O processo de atualização inclui a criptografia desses tokens para uma camada extra de segurança, e só é feito 100 registros de cada vez. Isso pode levar várias horas se houver um grande número de tokens.

A redução de um grande número de `oauth_tokens` no seu `oauth_token` A tabela pode evitar um grande atraso na atualização para a versão 2.4.6.

## Solução

Antes de iniciar uma atualização, primeiro verifique se [`CleanExpiredTokens.php`](https://github.com/magento/magento2/blob/2.4.5-p2/app/code/Magento/Integration/Cron/CleanExpiredTokens.php) [!DNL cron] tarefa em execução. Reduz o tamanho do `oauth_token` ao excluir a tabela `oauth_tokens` tokens, e já devem estar ativados por padrão.

Para acionar manualmente o [`CleanExpiredTokens.php`](https://github.com/magento/magento2/blob/2.4.5-p2/app/code/Magento/Integration/Cron/CleanExpiredTokens.php) [!DNL cron] tarefa, executar:
```bin/magento cron:run --group=default```

## Leitura relacionada

* [Serviços > [!DNL OAuth]](https://experienceleague.adobe.com/docs/commerce-admin/config/services/oauth.html) no guia Commerce Configuration Reference.
* [Guia de autenticação](https://developer.adobe.com/developer-console/docs/guides/authentication/) no guia do Adobe Developer.
