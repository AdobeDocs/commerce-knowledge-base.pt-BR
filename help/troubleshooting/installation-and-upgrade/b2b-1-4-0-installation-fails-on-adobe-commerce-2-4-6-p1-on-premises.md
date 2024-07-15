---
title: Falha na instalação do '[!DNL B2B] 1.4.0 no Adobe Commerce 2.4.6-p1 local'
description: Este artigo fornece uma solução alternativa para o problema local do Adobe Commerce 2.4.6-p1 em que a instalação da  [!DNL B2B] versão 1.4.0 falha.
feature: Install, Upgrade, B2B
role: Developer
exl-id: 4a557c13-7ec2-4cfe-b86e-bb0d1a441658
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 0%

---

# Falha na instalação do [!DNL B2B] 1.4.0 no Adobe Commerce 2.4.6-p1 local

Este artigo fornece uma solução alternativa para o problema local do Adobe Commerce 2.4.6-p1 em que a instalação da versão 1.4.0 do [!DNL B2B] falha.

## Produtos e versões afetados

* Adobe Commerce 2.4.6-p1 **no local**
* [!DNL B2B] versão 1.4.0

>[!NOTE]
>
>A versão 1.4.0 do [!DNL B2B] foi instalada com êxito no **Adobe Commerce Cloud 2.4.6-p1**.

## Problema

<u>Etapas a serem reproduzidas</u>:

1. Instale o Adobe Commerce 2.4.6-p1.

   ```terminal
   m2install.sh -s composer --ee -v 2.4.6-p1
   ```

1. Tente instalar a versão 1.4.0 de [!DNL B2B].

   ```terminal
   composer require magento/extension-b2b:1.4.0
   ```

<u>Resultados esperados</u>:

A versão 1.4.0 do [!DNL B2B] foi instalada com êxito no Adobe Commerce 2.4.6-p1.

<u>Resultados reais</u>:

A instalação falha com o seguinte erro:

```terminal
Your requirements could not be resolved to an installable set of packages.

  Problem 1
    - Root composer.json requires magento/extension-b2b 1.4.0 -> satisfiable by magento/extension-b2b[1.4.0].
    - magento/extension-b2b 1.4.0 requires magento/security-package-b2b 1.0.4-beta1 -> found magento/security-package-b2b[1.0.4-beta1] but it does not match your minimum-stability.


Installation failed, reverting ./composer.json and ./composer.lock to their original content.
```

## Solução alternativa

Êxito ao instalar ou atualizar para a versão 1.4.0 do [!DNL B2B] no Adobe Commerce 2.4.6-p1 adicionando dependências manuais para o pacote de segurança [!DNL B2B] com uma [marca de estabilidade](https://getcomposer.org/doc/04-schema.md#package-links).

1. No diretório de instalação do Adobe Commerce, atualize `composer.json` com as dependências necessárias:

   ```terminal
   composer require magento/module-re-captcha-company=1.0.3-beta1@beta magento/security-package-b2b=1.0.4-beta1@beta
   ```

   **Saída do comando:**

   ```terminal
   Running composer update magento/module-re-captcha-company magento/security-package-b2b
   Loading composer repositories with package information
   Updating dependencies
   Lock file operations: 2 installs, 0 updates, 0 removals
     - Locking magento/module-re-captcha-company (1.0.3-beta1)
     - Locking magento/security-package-b2b (1.0.4-beta1)
   Writing lock file
   Installing dependencies from lock file (including require-dev)
   Package operations: 2 installs, 0 updates, 0 removals
     - Downloading magento/module-re-captcha-company (1.0.3-beta1)
     - Installing magento/module-re-captcha-company (1.0.3-beta1): Extracting archive
     - Installing magento/security-package-b2b (1.0.4-beta1)
   1 package suggestions were added by new dependencies, use `composer suggest` to see details.
   Package sebastian/phpcpd is abandoned, you should avoid using it. No replacement was suggested.
   Generating autoload files
   132 packages you are using are looking for funding.
   Use the `composer fund` command to find out more!
   No security vulnerability advisories found
   ```

1. Atualize `composer.json` para adicionar [!DNL B2B] versão 1.4.0.

   ```terminal
   composer require magento/extension-b2b=1.4.0
   ```

   **Saída do comando:**

   ```terminal
   ./composer.json has been updated
   Running composer update magento/extension-b2b
   Loading composer repositories with package information
   Updating dependencies
   ...
   Generating autoload files
   132 packages you are using are looking for funding.
   Use the `composer fund` command to find out more!
   No security vulnerability advisories found
   ```

1. Conclua o processo de instalação ou atualização.

   * [Instalar [!DNL B2B] na infraestrutura em nuvem](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/b2b-module.html)
   * [Instalar no local](https://experienceleague.adobe.com/docs/commerce-admin/b2b/install.html)
