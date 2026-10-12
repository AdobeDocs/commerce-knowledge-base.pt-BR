---
title: Problema no token do GitHub e procedimentos principais do Composer
description: Este artigo fornece soluções para o problema de implantações com falha relacionadas a falhas de token Github causadas por chaves Composer desatualizadas.
exl-id: 202cb936-f9ba-49ea-bf0a-6e6994d2337a
feature: Identity Management
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
subfeature_v2:
  - id: 23bc8570-95c6-5ef5-a563-2e4a4e6b4853
    internal-label: Identity Management
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '278'
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

Se este método não funcionar, [envie um tíquete de suporte](https://experienceleague.adobe.com/pt-br/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#submit-ticket).

## Leitura relacionada

* [Blog do GitHub: por trás dos novos formatos de token de autenticação do GitHub](https://github.blog/2021-04-05-behind-githubs-new-authentication-token-formats/)
* [InfoQ.com artigo de notícias: GitHub altera o formato do token para melhorar a identificação, a verificação secreta e a entropia](https://www.infoq.com/news/2021/04/github-new-token-format/)
