---
title: Erros de atualização de patch e ferramentas ECE Adobe Commerce cloud infrastructure 2.2.x., 2.3.x
description: Este artigo fornece uma solução para o problema em que você vê mensagens de erro, incluindo "*falha ao abrir o fluxo:*" ou "*Não existe esse arquivo ou diretório*" ao tentar implantar atualizações para Ferramentas ECE, patches ou outras alterações.
exl-id: b1658001-0ffd-4f8a-a15f-d785efcee51f
feature: Cloud, Paas
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '191'
ht-degree: 0%

---

# Erros de atualização de patch e ferramentas ECE Adobe Commerce cloud infrastructure 2.2.x., 2.3.x

Este artigo fornece uma solução para o problema em que você vê mensagens de erro, incluindo &quot;*falha ao abrir o fluxo:*&quot; ou &quot;*Arquivo ou diretório inexistente*&quot; ao tentar implantar atualizações para Ferramentas ECE, patches ou outras alterações.

## Produtos e versões afetados

Adobe Commerce na infraestrutura em nuvem 2.2.x., 2.3.x

## Problema

Erros ao tentar implantar atualizações para ECE-Tools, patches ou outras alterações incluem: erros de PHP no Console da Nuvem e no `var/log/cloud.log`

```
W: PHP Warning: require(<path to file>): failed to open stream: No such file or directory in <path to file> on line 70
W: PHP Fatal error: require(): Failed opening required '<path to file>;'
(include_path='<path to file>') in <path to file> on line 70

Warning: require(/app/vendor/composer/../../app/etc/NonComposerComponentRegistration.php):
failed to open stream: No such file or directory in /app/vendor/composer/autoload_real.php
on line 70

Fatal error: require(): Failed opening required '/app/vendor/composer/../../app/etc/NonComposerComponentRegistration.php'
(include_path='/app/vendor/magento/zendframework1/library:.:/usr/share/php')
in /app/vendor/composer/autoload_real.php on line 70

E: Error building project: Step failed with status code 255.
```

Erros do log de exceções:

```
CRITICAL:
error: <path to missing file>: No such file or directory
```

```
W: Generating optimized autoload files
W: PHP Warning: Uncaught ErrorException: require(<path to file>):
failed to open stream: No such file or directory in <path to file>
```

```
PHP Warning: Uncaught Exception: Warning: require(/app/setup/config/application.config.php):
failed to open stream: No such file or directory in /app/vendor/magento/framework/Console/Cli.php
on line 63 in /app/vendor/magento/framework/App/ErrorHandler.php:61
```

```
[Symfony\Component\Console\Exception\CommandNotFoundException]
 W: There are no commands defined in the "module" namespace.
```

## Causa

Configuração incorreta do arquivo `composer.json`.

## Solução

Se uma configuração estiver ausente no arquivo `composer.json`, alguns diretórios não serão copiados da Base de Código Adobe Commerce. O pacote e a atualização/correção não podem ser aplicados porque os arquivos não serão encontrados.

Altere sua seção extra para corresponder à fornecida abaixo e tente implantar novamente.

```
"extra":{
  "magento-force": true,
  "magento-deploystrategy": "copy"
}
```

## Leitura relacionada

* [Atualizações e correções](https://experienceleague.adobe.com/pt-br/docs/commerce-cloud-service/user-guide/develop/upgrade/best-practices) em nossa documentação para desenvolvedores.
