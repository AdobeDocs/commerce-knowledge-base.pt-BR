---
title: O comando de instalação do Composer substitui o arquivo .gitignore, Adobe Commerce
description: Este artigo fornece uma solução para quando um arquivo '.gitignore' rastreado é substituído pelo composer no Adobe Commerce na infraestrutura de nuvem 2.4.2-p1 e 2.3.7.
exl-id: b0604bae-d630-4292-88d7-6945db30fcf4
feature: Install, Upgrade
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 6388cf7b-8a81-5248-a1e4-7bb57bbe250f
    internal-label: Install
  - id: a8ae7a5a-6cdc-5922-bd0d-6feb44b04984
    internal-label: Upgrade
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '163'
ht-degree: 0%
---
# O comando de instalação do Composer substitui o arquivo .gitignore, Adobe Commerce

Este artigo fornece uma solução para quando um arquivo `.gitignore` rastreado é substituído pelo compositor no Adobe Commerce na infraestrutura de nuvem 2.4.2-p1 e 2.3.7.

## Produtos e versões afetados

Adobe Commerce na infraestrutura em nuvem 2.4.2-p1 e 2.3.7.

## Problema

O arquivo `.gitignore` está sendo substituído durante a execução do comando de instalação do compositor.

<u>Etapas a serem reproduzidas</u>:


1. Crie um diretório vazio para o espaço de trabalho.
1. Execute este comando no diretório raiz:

   ```bash
   composer create-project --repository-url=https://repo.magento.com/ magento/project-community-edition:2.4.2-p1.
   ```

   \# ou 2.3.7

1. Em seguida, execute os seguintes comandos:
   1. `echo "/this/line/should/stay" >> .gitignore`
   1. `git init`
   1. `git add * && git add .*`
   1. `git commit -m "Init"` # arquivo comprometido com o repositório
   1. `rm -rf vendor/*`
   1. `composer install`
   1. `git diff`

      ```git
      diff --git a/.gitignore b/.gitignore
      index c144521..7092a56 100644
      --- a/.gitignore
      +++ b/.gitignore
      @@ -70,4 +70,3 @@ atlassian*
      /generated/*
      !/generated/.htaccess
      .DS_Store
      -/this/line/should/stay
      ```

<u>Resultado esperado</u>:

`.gitignore` não foi substituído pelo compositor.

<u>Resultado real</u>:

`.gitignore` é substituído por cada execução de instalação do compositor.

## Solução

Para manter seu `.gitignore file` personalizado, você precisa ignorá-lo na seção `magento-deploy-ignore`.

```git
{
...
"extra": {
    "magento-deploy-ignore": {
        "*": [
            "/.gitignore"
        ]
    }
    ...
}
```


## Leitura relacionada

* [O arquivo .gitignore rastreado foi substituído pelo compositor!](https://github.com/magento/magento2/issues/32888) no GitHub do Magento2.
