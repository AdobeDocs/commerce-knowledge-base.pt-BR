---
title: Durante a instalação, exceção SessionHandler::read()
description: "Este artigo fornece uma correção para um erro **SessionHandler::read()** durante a instalação do Adobe Commerce."
source-git-commit: 5cec04f8c4f80d34fc26b06eb929960ce21e2dc0
workflow-type: tm+mt
source-wordcount: '218'
ht-degree: 0%

---


# Durante a instalação, exceção SessionHandler::read()

Este artigo fornece uma correção para uma exceção **SessionHandler::read()** erro durante a instalação do Adobe Commerce.

## Problema

Na última etapa de instalação do Adobe Commerce, a seguinte exceção é exibida:

```temrinal
exception 'Exception' with message 'Warning: SessionHandler::read():
open(..) failed: No such file or directory (2) ../magento2/lib/internal/Magento/Framework/Session/SaveHandler.php on line 74'
in ../magento2/lib/internal/Magento/Framework/App/ErrorHandler.php:67
```

>[!NOTE]
>
>Este erro ocorre somente em versões de código anteriores a 28 de setembro de 2015. Se você instalar o código datado de 29 de setembro ou posterior, esse erro não deverá ocorrer. Para obter mais informações sobre as opções de configuração para Redis, consulte [Configurar Redis](https://devdocs.magento.com/guides/v2.3/config-guide/redis/config-redis.html) na documentação do desenvolvedor. Para obter mais informações sobre como especificar Redis usando o instalador de linha de comando, consulte [tópico de instalação](https://devdocs.magento.com/guides/v2.3/install-gde/install/cli/install-cli-install.html) ou o [tópico configuração de implantação](https://devdocs.magento.com/guides/v2.3/install-gde/install/cli/install-cli-subcommands-deployment.html#instgde-cli-subcommands-configphp) na documentação do desenvolvedor.

## Causa

Isso acontece quando o `session.save_handler` O parâmetro PHP está configurado para algum outro armazenamento de sessão que `files` (por exemplo, `redis`, `memcached`e assim por diante). Este é um problema conhecido que estamos trabalhando para resolver.

## Soluções:

* Atualize seu código Adobe Commerce. Consulte [Guia de instalação > Atualizar o software Adobe Commerce](https://devdocs.magento.com/guides/v2.3/install-gde/install/cli/install-cli-uninstall.html#instgde-install-magento-update) na documentação do desenvolvedor.
* Use a seguinte solução alternativa com o código existente:

## Localizar `php.ini` {#locate-php-ini}

Localizar `php.ini` digitando o seguinte comando:

```php
php -i | grep "Loaded Configuration File"
```

Os locais típicos são:

* Ubuntu: `/etc/php5/cli/php.ini`
* CentOS: `/etc/php.ini`

## Solução alternativa {#workaround}

1. Como usuário com `root` privilégios, abrir `php.ini` em um editor de texto.
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
