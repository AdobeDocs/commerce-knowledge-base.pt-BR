---
title: Problema no token do GitHub e procedimentos principais do Composer
description: Este artigo fornece soluções para o problema de implantações com falha relacionadas a falhas de token Github causadas por chaves Composer desatualizadas.
exl-id: 202cb936-f9ba-49ea-bf0a-6e6994d2337a
feature: Identity Management
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 0%

---

# Problema no token do GitHub e procedimentos principais do Composer

Este artigo fornece soluções para o problema de implantações com falha relacionadas a falhas de token Github causadas por chaves Composer desatualizadas.

## Produtos e versões afetados

* Adobe Commerce na infraestrutura em nuvem, [todas as versões com suporte](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)
* Composer versões 1.10.20 e anteriores

>[!NOTE]
>
>Os comerciantes locais do Adobe Commerce devem consultar seu provedor de host para garantir que estejam usando o Composer versão 1.10.21 ou superior devido às alterações de formato de token introduzidas pelo Git.

## Problema

As implantações falham e os logs de implantação contêm informações semelhantes às seguintes:

*Erro fatal: Uncaught UnexpectedValueException: Seu token oauth do github para github.com contém caracteres inválidos: &quot;ghp_xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx&quot; em /app/vendor/composer/composer/src/Composer/IO/BaseIO.php:129*

## Causa

Chaves Composer desatualizadas causam falhas no token Github, que resultam em implantações com falha.

## Solução

Para resolver o problema, atualize sua versão do Composer para 1.10.22:

1. Em seu ambiente local, execute `composer require “composer/composer”:”>1.10.21`.
1. Isso adiciona o requisito para a versão do pacote do Composer. Verificar o arquivo de bloqueio - a versão `composer/composer` deve ser 1.0.22 ou superior.
1. Confirme `composer.json` e `composer.lock` e envie uma implantação por push.

Se este método não funcionar, [envie um tíquete de suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

## Leitura relacionada

* [Blog do Github: por trás dos novos formatos de token de autenticação do GitHub](https://github.blog/2021-04-05-behind-githubs-new-authentication-token-formats/)
* [Artigo de notícias do InfoQ.com: O GitHub altera o formato do token para melhorar a identificação, a verificação secreta e a entropia](https://www.infoq.com/news/2021/04/github-new-token-format/)
