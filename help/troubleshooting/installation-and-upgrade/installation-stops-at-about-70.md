---
title: A instalação pára em cerca de 70%
description: Este artigo fornece uma correção para quando a instalação é interrompida em cerca de 70%.
exl-id: 04aa3572-3c42-4565-9f7f-b4d90df96df2
feature: Install, Upgrade
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 0%

---

# A instalação pára em cerca de 70%

Este artigo fornece uma correção para quando a instalação é interrompida em cerca de 70%.

## Problema

Durante a instalação usando o Assistente de configuração, o processo é interrompido em cerca de 70% (com ou sem dados de amostra). Nenhum erro é exibido na tela.

## Causa

Causas comuns para esse problema:

* A configuração do PHP para [`max_execution_time`](http://php.net/manual/en/info.configuration.php#ini.max-execution-time)
* Valores de tempo limite para nginx e Verniz

## Solução:

Defina todos os itens a seguir conforme apropriado.

### Todos os servidores Web e Verniz {#all-web-servers-and-varnish}

1. Localize seu `php.ini` usando um arquivo [`phpinfo.php`](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/installation-guide/prerequisites/optional-software).
1. Como um usuário com privilégios `root`, abra o `php.ini` em um editor de texto.
1. Localize a configuração `max_execution_time`.
1. Altere seu valor para `18000`.
1. Salve as alterações em `php.ini` e saia do editor de texto.
1. Reiniciar o Apache:

   * CentOS: `service httpd restart`
   * Ubuntu: `service apache2 restart`

   Se você usar nginx ou Verniz, continue com as seções a seguir.

### somente nginx {#nginx-only}

Se você usa nginx, use nosso `nginx.conf.sample` incluído ou adicione uma configuração de tempo limite no arquivo de configuração do host nginx à seção `location ~ ^/setup/index.php` da seguinte maneira:

```php
location ~ ^/setup/index.php {
    .....................
    fastcgi_read_timeout 600s;
       fastcgi_connect_timeout 600s;
}
```

Reiniciar o nginx: `service nginx restart`

### Somente verniz {#varnish-only}

Se você usar Verniz, edite `default.vcl` e adicione um valor de limite de tempo à estrofe `backend` da seguinte maneira:

```php
backend default {
.....................
      .first_byte_timeout = 600s;
}
```

Reinicie o Varnish.

```php
service varnish restart
```
