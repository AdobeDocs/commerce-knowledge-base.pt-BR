---
title: O comando de instalação do Composer substitui o arquivo .gitignore, Adobe Commerce
description: Este artigo fornece uma solução para quando um arquivo '.gitignore' rastreado é substituído pelo composer no Adobe Commerce na infraestrutura de nuvem 2.4.2-p1 e 2.3.7.
exl-id: b0604bae-d630-4292-88d7-6945db30fcf4
feature: Install, Upgrade
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '159'
ht-degree: 0%

---

# O comando de instalação do Composer substitui o arquivo .gitignore, Adobe Commerce

Este artigo fornece uma solução para quando um `.gitignore` o arquivo é substituído pelo composer no Adobe Commerce na infraestrutura em nuvem 2.4.2-p1 e 2.3.7.

## Produtos e versões afetados

Adobe Commerce na infraestrutura em nuvem 2.4.2-p1 e 2.3.7.

## Problema

`.gitignore` o arquivo está sendo sobrescrito ao executar o comando de instalação do composer.

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

`.gitignore` não é substituído pelo compositor.

<u>Resultado real</u>:

`.gitignore` é substituído por cada execução de instalação do composer.

## Solução

Para manter sua `.gitignore file` você precisa ignorá-lo na variável `magento-deploy-ignore` seção.

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

* [O arquivo .gitignore rastreado é substituído pelo compositor!](https://github.com/magento/magento2/issues/32888) no GitHub Magento2.
