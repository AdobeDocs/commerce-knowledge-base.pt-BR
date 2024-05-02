---
title: Falha na instalação; não é possível criar o install.log
description: Este artigo fornece uma correção para uma instalação com falha porque o Assistente de configuração não criou o "install.log" durante a instalação.
exl-id: ff614018-8e49-4170-a806-8ebdc91ae8a9
feature: Install, Logs, Upgrade
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 0%

---

# Falha na instalação; não é possível criar o install.log

Este artigo fornece uma correção para uma instalação com falha porque o Assistente de configuração não cria o `install.log` durante a instalação.

## Problema

A execução simultânea de processos do Adobe Commerce pode causar problemas ao criar o log de instalação. (Por exemplo, duas instalações diferentes em páginas de guia separadas.)

## Causa

Instalação-failures-cannot-create-install.log Revise suas configurações para `open_basedir` in `php.ini`. O Assistente de configuração usa o [sys\_get\_temp\_dir ( void )](https://php.net/manual/en/function.sys-get-temp-dir.php) Chamada PHP para obter o valor do diretório temporário. Se [open\_basedir](http://php.net/manual/en/ini.core.php#ini.open-basedir) está definido para recusar conexões com um diretório especificado por `sys_get_temp_dir`, a instalação falha.
Revise suas configurações para `open_basedir` in `php.ini`. O Assistente de configuração usa o [sys\_get\_temp\_dir ( void )](https://php.net/manual/en/function.sys-get-temp-dir.php) Chamada PHP para obter o valor do diretório temporário. Se [open\_basedir](https://php.net/manual/en/ini.core.php#ini.open-basedir) está definido para recusar conexões com um diretório especificado por `sys_get_temp_dir`, a instalação falha.


## Solução

Para resolver o problema, altere o valor de `open_basedir` e reinicie o servidor web.

Se não tiver certeza de como alterar esse valor, siga as etapas abaixo:

1. Se ainda não tiver feito isso, crie [phpinfo.php](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/optional.html#install-optional-phpinfo).
1. Insira o seguinte URL no campo de endereço ou local do navegador: `https://<your web server IP or hostname>/<path to docroot>/phpinfo.php`
1. Procure a localização de `php.ini`.     `php.ini` é normalmente especificado como **Arquivo de configuração carregado** nos resultados exibidos.
1. Como um usuário com privilégios raiz, abra `php.ini` em um editor de texto.
1. Localize o valor de `open_basedir` e alterá-lo.
1. Salvar as alterações em `php.ini`.
1. Reinicie o servidor Web.
