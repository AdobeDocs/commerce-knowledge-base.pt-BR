---
title: Falha na instalação; não é possível criar o install.log
description: Este artigo fornece uma correção para uma instalação com falha porque o Assistente de configuração não criou o "install.log" durante a instalação.
exl-id: ff614018-8e49-4170-a806-8ebdc91ae8a9
feature: Install, Logs, Upgrade
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 0%

---

# Falha na instalação; não é possível criar o install.log

Este artigo fornece uma correção para uma instalação com falha porque o Assistente para Instalação não cria o `install.log` durante a instalação.

## Problema

A execução simultânea de processos do Adobe Commerce pode causar problemas ao criar o log de instalação. (Por exemplo, duas instalações diferentes em páginas de guia separadas.)

## Causa

Installation-failures-cannot-create-install.log
Revise sua configuração para `open_basedir` em `php.ini`. O Assistente de Instalação usa a chamada PHP [sys\_get\_temp\_dir ( void )](https://php.net/manual/en/function.sys-get-temp-dir.php) para obter o valor do diretório temporário. Se [open\_basedir](http://php.net/manual/en/ini.core.php#ini.open-basedir) estiver definido para recusar conexões com um diretório especificado por `sys_get_temp_dir`, a instalação falhará.
Revise sua configuração para `open_basedir` em `php.ini`. O Assistente de Instalação usa a chamada PHP [sys\_get\_temp\_dir ( void )](https://php.net/manual/en/function.sys-get-temp-dir.php) para obter o valor do diretório temporário. Se [open\_basedir](https://php.net/manual/en/ini.core.php#ini.open-basedir) estiver definido para recusar conexões com um diretório especificado por `sys_get_temp_dir`, a instalação falhará.


## Solução

Para resolver o problema, altere o valor de `open_basedir` e reinicie o servidor Web.

Se não tiver certeza de como alterar esse valor, siga as etapas abaixo:

1. Se ainda não tiver feito isso, crie [phpinfo.php](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/installation-guide/prerequisites/optional-software).
1. Digite a seguinte URL no campo de endereço ou local do seu navegador: `https://<your web server IP or hostname>/<path to docroot>/phpinfo.php`
1. Procure a localização de `php.ini`.     `php.ini` é normalmente especificado como **Arquivo de Configuração Carregado** nos resultados exibidos.
1. Como um usuário com privilégios raiz, abra `php.ini` em um editor de texto.
1. Localize o valor de `open_basedir` e altere-o.
1. Salve as alterações em `php.ini`.
1. Reinicie o servidor Web.
