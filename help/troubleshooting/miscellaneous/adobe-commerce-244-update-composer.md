---
title: Problemas de plug-ins do Composer ao atualizar para o Adobe Commerce 2.4.4
description: Este artigo fornece uma solução para evitar o problema com plug-ins do Composer ao atualizar do Adobe Commerce 2.4.3 e anterior para o Adobe Commerce 2.4.4 ou superior (quando versões futuras forem lançadas).
exl-id: 7502ca9e-c307-4e8a-aa1d-4886e7be25da
feature: Upgrade
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '276'
ht-degree: 0%

---

# Problemas de plug-ins do Composer ao atualizar para o Adobe Commerce 2.4.4

Este artigo fornece uma solução para evitar problemas com plug-ins do Composer ao atualizar do Adobe Commerce 2.4.3 e anterior para o Adobe Commerce 2.4.4 ou superior (quando versões futuras forem lançadas).

## Produtos e versões afetados

* Adobe Commerce no local, qualquer versão ao atualizar para a versão 2.4.4 ou superior (quando lançado)
* Adobe Commerce na infraestrutura em nuvem, qualquer versão ao atualizar para a versão 2.4.4 ou superior (quando lançado)
* Magento Open Source, qualquer versão ao atualizar para a versão 2.4.4 ou superior (quando lançado)

## Problema

Ao atualizar para o Adobe Commerce 2.4.4 ou superior após julho de 2022, você poderá receber um aviso do compositor sobre plug-ins.

<u>Etapas a serem reproduzidas</u>:

Pré-requisitos: o Adobe Commerce 2.4.3 ou anterior está instalado.

1. Inicie a atualização conforme descrito em [Executar uma atualização](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/implementation/perform-upgrade.html).
1. Execute o comando `composer update` para atualizar o aplicativo Adobe Commerce.

<u>Resultados esperados</u>:

Atualização bem-sucedida.

<u>Resultados reais</u>:

A instalação falha com um erro semelhante ao seguinte:

```bash
Writing lock file
Installing dependencies from lock file (including require-dev)
Package operations: 591 installs, 0 updates, 0 removals
  - Installing laminas/laminas-dependency-plugin (2.2.0): Extracting archive
laminas/laminas-dependency-plugin contains a Composer plugin which is currently not in your allow-plugins config. See https://getcomposer.org/allow-plugins
Do you trust "laminas/laminas-dependency-plugin" to execute code and wish to enable it now? (writes "allow-plugins" to composer.json) [y,n,d,?] y
Plugin initialization failed (require(app/etc/NonComposerComponentRegistration.php): failed to open stream: No such file or directory), uninstalling plugin
  - Removing laminas/laminas-dependency-plugin (2.2.0)
    Install of laminas/laminas-dependency-plugin failed


  [ErrorException]
  require(app/etc/NonComposerComponentRegistration.php): failed to open stream: No such file or directory
```

## Causa

Depois de julho de 2022, o Composer alterará o valor padrão da [`allow-plugins` opção](https://getcomposer.org/doc/06-config.md#allow-plugins) para `{}` e os plug-ins não carregarão mais, a menos que permitido.

## Solução

Adicione o seguinte ao arquivo `composer.json`, dependendo de como você instalou o Adobe Commerce:

* Se o projeto foi criado [usando o `composer create-project` comando](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/composer#get-the-metapackage):

  ```json
  "config": {
      "allow-plugins": {
          "dealerdirect/phpcodesniffer-composer-installer": true,
          "laminas/laminas-dependency-plugin": true,
          "magento/*": true
      }
  }
  ```

* Se o projeto foi criado por outra forma e não tem `"dealerdirect/phpcodesniffer-installer"` na seção `"require-dev"`:

  ```json
  "config": {
      "allow-plugins": {
          "laminas/laminas-dependency-plugin": true,
          "magento/*": true
      }
  }
  ```

Depois de atualizar o arquivo `composer.json`, execute o comando `composer update` e reinicie o processo de atualização.
