---
title: Problemas de verificação de preparação de permissões de arquivo
description: '"Este artigo fornece uma correção para problemas de verificação de preparação de permissões de arquivo. Os diretórios no sistema de arquivos do Adobe Commerce devem ser graváveis pelo usuário do servidor da Web e pelo proprietário do sistema de arquivos do Adobe Commerce, se aplicável. Um erro semelhante ao seguinte é exibido no Assistente de configuração da Web se suas permissões não estiverem definidas corretamente:'''
exl-id: 252e6e7d-5269-44ce-b3ce-6fc2ea6a1c5c
feature: Roles/Permissions
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '308'
ht-degree: 0%

---

# Problemas de verificação de preparação de permissões de arquivo

Este artigo fornece uma correção para problemas de verificação de preparação de permissões de arquivo. Os diretórios no sistema de arquivos do Adobe Commerce devem ser graváveis pelo usuário do servidor da Web e pelo proprietário do sistema de arquivos do Adobe Commerce, se aplicável. Um erro semelhante ao seguinte é exibido no Assistente de configuração da Web se suas permissões não estiverem definidas corretamente:

![install_rc_file-perms.png](assets/install_rc_file-perms.png)

A maneira de resolver o problema depende da configuração de um ou dois usuários:

* *Um usuário* significa que você fez logon no servidor do Adobe Commerce como o mesmo usuário que também executa o servidor da web. Esse tipo de configuração é comum em ambientes de hospedagem compartilhados.
* *Dois usuários* significa que você normalmente *não é possível* efetue login como, ou alterne para, o usuário do servidor Web. Normalmente, você faz logon como um usuário e executa o servidor Web como um usuário diferente. Isso é típico em hospedagem privada ou se você tem seu próprio servidor.

## Resolução para um usuário

Se você tiver acesso à linha de comando, digite o seguinte comando, supondo que o Adobe Commerce esteja instalado em `/var/www/html/magento2`:

```bash
$ cd /var/www/html/magento2 && find var vendor pub/static pub/media app/etc -type f -exec chmod g+w {} + && find var vendor pub/static pub/media app/etc -type d -exec chmod g+w {} + && chmod u+x bin/magento
```

Se você não tiver acesso de linha de comando, use um cliente FTP ou um aplicativo gerenciador de arquivos fornecido pelo seu provedor de hospedagem para definir permissões.

## Resolução para dois usuários

Para informar opcionalmente todos os comandos em uma linha, informe o seguinte, considerando que o Adobe Commerce esteja instalado em `/var/www/html/magento2` e o nome do grupo do servidor web é `apache`:

```bash
$ cd /var/www/html/magento2 && find var vendor pub/static pub/media app/etc -type f -exec chmod g+w {} + && find var vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} + && chown -R :apache . && chmod u+x bin/magento
```

Se as permissões do sistema de arquivos do evento forem definidas incorretamente e não puderem ser alteradas pelo proprietário do sistema de arquivos do Adobe Commerce, você poderá inserir o comando como um usuário com `root` privilégios:

```bash
$ cd /var/www/html/magento2 && sudo find var vendor
  pub/static pub/media app/etc -type f -exec chmod g+w {} + && sudo find
  var vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} + &&
  sudo chown -R :apache . && sudo chmod u+x bin/magento
```
