---
title: Falha na instalação; não é possível criar o install.log
description: Este artigo fornece uma correção para uma instalação com falha porque o Assistente de configuração não criou o "install.log" durante a instalação.
exl-id: ff614018-8e49-4170-a806-8ebdc91ae8a9
feature: Install, Logs, Upgrade
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 6388cf7b-8a81-5248-a1e4-7bb57bbe250f
    internal-label: Install
  - id: a8ae7a5a-6cdc-5922-bd0d-6feb44b04984
    internal-label: Upgrade
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
subfeature_v2:
  - id: 3c398179-d35a-51ba-b317-6c5b95feef5e
    internal-label: Logs
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '283'
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
1. Procure o local de `php.ini`. `php.ini` geralmente é especificado como **Arquivo de Configuração Carregado** nos resultados exibidos.
1. Como um usuário com privilégios raiz, abra `php.ini` em um editor de texto.
1. Localize o valor de `open_basedir` e altere-o.
1. Salve as alterações em `php.ini`.
1. Reinicie o servidor Web.
