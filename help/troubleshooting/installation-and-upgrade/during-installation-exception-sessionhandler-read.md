---
title: Durante a instalação, exceção SessionHandler::read()
description: Este artigo fornece uma correção para um erro **SessionHandler::read()** durante a instalação do Adobe Commerce.
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '218'
ht-degree: 0%

---


# Durante a instalação, exceção SessionHandler::read()

Este artigo fornece uma correção para um erro de exceção **SessionHandler::read()** durante a instalação do Adobe Commerce.

## Problema

Na última etapa de instalação do Adobe Commerce, a seguinte exceção é exibida:

```temrinal
exception 'Exception' with message 'Warning: SessionHandler::read():
open(..) failed: No such file or directory (2) ../magento2/lib/internal/Magento/Framework/Session/SaveHandler.php on line 74'
in ../magento2/lib/internal/Magento/Framework/App/ErrorHandler.php:67
```

>[!NOTE]
>
>Este erro ocorre somente em versões de código anteriores a 28 de setembro de 2015. Se você instalar o código datado de 29 de setembro ou posterior, esse erro não deverá ocorrer. Para obter mais informações sobre as opções de configuração para Redis, consulte [Configurar Redis](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/configuration-guide/cache/redis/config-redis) na documentação do desenvolvedor. Para obter mais informações sobre como especificar Redis usando o instalador de linha de comando, consulte o [tópico de instalação](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/installation-guide/advanced) ou o [tópico de configuração de implantação](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/installation-guide/tutorials/deployment) na documentação do desenvolvedor.

## Causa

Isso acontece quando o parâmetro PHP `session.save_handler` é definido como algum outro armazenamento de sessão que `files` (por exemplo, `redis`, `memcached`, e assim por diante). Este é um problema conhecido que estamos trabalhando para resolver.

## Soluções:

* Atualize seu código Adobe Commerce. Consulte o [Guia de Instalação > Atualizar o software Adobe Commerce](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/installation-guide/tutorials/uninstall) na documentação do desenvolvedor.
* Use a seguinte solução alternativa com o código existente:

## Localizar `php.ini` {#locate-php-ini}

Localize `php.ini` inserindo o seguinte comando:

```php
php -i | grep "Loaded Configuration File"
```

Os locais típicos são:

* Ubuntu: `/etc/php5/cli/php.ini`
* CentOS: `/etc/php.ini`

## Solução alternativa {#workaround}

1. Como um usuário com privilégios `root`, abra o `php.ini` em um editor de texto.
1. Localizar `session.save_handler`
1. Defina-o de qualquer uma das seguintes maneiras:
   * Para comentar:

     ```php
     ;session.save_path = <path>
     ```

   * Para defini-lo como um caminho do sistema de arquivos:

     ```php
     session.save_handler = files
     ```
