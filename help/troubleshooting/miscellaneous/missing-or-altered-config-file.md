---
title: Arquivo de configuração ausente ou alterado
description: Resolva o problema com o arquivo de configuração ausente ou alterado do Adobe Commerce.
exl-id: d80bf981-8ba6-4357-a841-57bf5d3f2a3f
feature: Configuration
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 0%

---

# Arquivo de configuração ausente ou alterado

Este artigo fala sobre como resolver o problema em que seus arquivos de configuração foram alterados ou estão ausentes.

## Produtos e versões afetados

* Adobe Commerce na infraestrutura em nuvem, todas as versões

## Problema

Os arquivos de configuração `config.php` e/ou `env.php` foram alterados incorretamente ou estão ausentes.

## Solução

O processo de implantação cria um arquivo de backup para cada arquivo de configuração:

* `app/etc/config.php.bak` — contém configurações específicas do sistema e é gerado automaticamente durante a compilação se não existir
* `app/etc/env.php.bak` — contém dados confidenciais de configuração

Você pode restaurá-los usando o comando ECE-tools `backup:restore`.

Os arquivos BAK são um produto do processo de implantação. Se você alterar manualmente um arquivo de configuração após a implantação, suas alterações não serão refletidas nos arquivos BAK existentes.

Para restaurar os arquivos de configuração:

1. Faça logon no repositório remoto usando o [SSH](https://experienceleague.adobe.com/pt-br/docs/commerce-cloud-service/user-guide/develop/secure-connections#ssh).
1. Listar os arquivos de backup disponíveis.

   ```
   ./vendor/bin/ece-tools backup:list
   ```

   ```
   The list of backup files:
   app/etc/env.php
   app/etc/config.php
   ```

1. Restaure os arquivos de configuração.

   ```
   ./vendor/bin/ece-tools backup:restore
   ```

   Você receberá uma lista dos arquivos de configuração existentes afetados pela restauração.

   ```
   app/etc/env.php file exists! If you want to rewrite existed files use --force
   app/etc/config.php file exists! If you want to rewrite existed files use --force
   ```

1. Use a opção `--force` para substituir todos os arquivos.

   ```
   ./vendor/bin/ece-tools backup:restore --force
   ```

   ```
   Command backup:restore with option --force will rewrite your existed files. Do you want to continue [y/N]?y
   Backup file app/etc/env.php was restored.
   Backup file app/etc/config.php was restored.
   ```

1. Como opção, você pode restaurar um arquivo de configuração específico.

   ```
   ./vendor/bin/ece-tools backup:restore --force --file=app/etc/config.php
   ```

   ```
   Command backup:restore with option --force will rewrite your existed files. Do you want to continue [y/N]?y
   Backup file app/etc/config.php was restored.
   ```
