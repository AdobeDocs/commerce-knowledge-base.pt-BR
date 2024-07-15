---
title: Extensão mcrypt do PHP não instalada corretamente
description: Extensão mcrypt do PHP não instalada corretamente
exl-id: 1010349e-6631-4a05-8883-5cc903d67534
feature: Extensions, Install
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 0%

---

# Extensão mcrypt do PHP não instalada corretamente

>[!WARNING]
>
>OBSERVAÇÃO: O recurso mcrypt library foi [descontinuado do PHP 7.1 e foi removido do PHP 7.2](https://www.php.net/manual/en/intro.mcrypt.php).

## Detalhe

Os erros podem incluir o seguinte:

```php
exception 'Exception' with message 'PHP Warning: [PHP](https://glossary.magento.com/php) Startup: Unable to load dynamic [library](https://glossary.magento.com/library) '/usr/lib/php5/20121212/mcrypt.so' - /usr/lib/php5/20121212/mcrypt.so: cannot open shared object file: No such file or directory
```

```php
Installing data fixtures:
/usr/bin/php -f '/Users/username/www/magento/dev/shell/run_data_fixtures.php' -- --bootstrap='MAGE_DIRS[base][path]=/Users/username/www/magento' 2>&1
[ERROR] [exception](https://glossary.magento.com/exception) 'Exception' with message '
Fatal error: Uncaught exception 'Exception' with message 'Module 'Magento_Core' depends on 'mcrypt' PHP [extension](https://glossary.magento.com/extension) that is not loaded.'
```

```php
======================================================================
   The application has thrown an exception!
======================================================================
 Magento\Framework\Exception
 Command returned non-zero exit code:
`/usr/bin/php5 -f '/var/www/magento2/dev/shell/run_data_fixtures.php' -- --bootstrap='MAGE_DIRS[base][path]=/var/www/magento2' 2>&1`
```

## Descrição

Particularmente em sistemas de desenvolvedores que incluem uma &quot;pilha&quot; de Linux/Apache/MySQL/PHP (LAMP) separada do sistema operacional, é possível que o mcrypt não esteja instalado ou esteja instalado no caminho da pilha do LAMP, mas não no caminho do sistema operacional.

Como resultado, o instalador do Adobe Commerce não pode localizar a extensão e a instalação falha.

## Sugestão

Determine se a extensão mcrypt é carregada de qualquer uma das seguintes maneiras:

* Configure um arquivo [phpinfo.php](http://kb.mediatemple.net/questions/764/How+can+I+create+a+phpinfo.php+page%3F#gs) no diretório raiz do servidor Web e examine a saída em um navegador Web.
* Execute o seguinte comando:    `$ php -r "phpinfo();" | grep mcrypt`

Se o mcrypt estiver *não* instalado, mensagens semelhantes serão exibidas:

```php
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20121212/mcrypt.so' - /usr/lib/php5/20121212/mcrypt.so: cannot open shared object file: No such file or directory in Unknown on line 0
```

Em alguns casos, talvez seja necessário instalar o software Adobe Commerce a partir da [linha de comando](https://devdocs.magento.com/guides/v2.3/install-gde/install/cli/install-cli.html) e especificar o caminho completo para a pilha de LAMP que tem o mcrypt instalado.
