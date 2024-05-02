---
title: Resolver um erro de deslocamento ilegal
description: Este artigo fornece uma solução para quando, no Adobe Commerce 2.1 ou posterior, você recebe um erro Resolver um deslocamento ilegal ao criar um novo produto no Administrador do Commerce.
exl-id: 62d16d3c-7f4b-45e9-ae4b-fe2b58cc3620
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 0%

---

# Resolver um erro de deslocamento ilegal

Este artigo fornece uma solução para quando, no Adobe Commerce 2.1 ou posterior, você recebe um erro Resolver um deslocamento ilegal ao criar um novo produto no Administrador do Commerce.

No Adobe Commerce 2.1 ou posterior, ao criar um novo produto no Commerce Admin, o seguinte erro pode ser exibido:

```text
Warning: Illegal string offset 'is_in_stock' in [...]/vendor/
magento/module-catalog-inventory/Ui/DataProvider/Product/Form/
Modifier/AdvancedInventory.php on line 87
```

## Detalhe

O Adobe Commerce 2.1 e versões posteriores usam comentários de código PHP no `getDocComment` chamada de validação na [`getExtensionAttributes`](https://github.com/magento/magento2/blob/2.3/lib/internal/Magento/Framework/Api/ExtensionAttributesFactory.php#L64-L73) método em `Magento\Framework\Api\ExtensionAttributesFactory.php`.

Se você ativou o OPcache do PHP (o que recomendamos), este erro é exibido porque, por padrão, a configuração do OPcache [`opcache.save_comments`](http://php.net/manual/en/opcache.configuration.php#ini.opcache.save_comments) está desativado.

## Solução alternativa

Para resolver o problema, localize as definições de configuração do OPcache e ative `opcache.save_comments` do seguinte modo:

### Etapa 1: Localizar a configuração do OPcache

#### Para localizar as definições de configuração do OPcache:

Normalmente, as configurações de OPcache do PHP estão localizadas em `php.ini` ou `opcache.ini`. A localização pode depender do seu sistema operacional e da versão do PHP. O arquivo de configuração do OPcache pode ter um `[opcache]` seção ou configurações como `opcache.enable`.

Use as diretrizes a seguir para encontrá-la:

* Apache Web Server:<br>

No Ubuntu com Apache, as configurações do OPcache normalmente estão localizadas em `php.ini`.<br>
Para CentOS com Apache ou nginx, as configurações de OPcache normalmente estão localizadas em `/etc/php.d/opcache.ini`.<br>
Caso contrário, use o seguinte comando para localizá-lo:

```bash
    $ sudo find / -name 'opcache.ini'
```

* nginx web server com PHP-FPM: `/etc/php5/fpm/php.ini`.

Se tiver mais de um `opcache.ini`, modifique todos eles.


### Etapa 2: Ativar `opcache.save_comments`

1. Abra o arquivo de configuração do OPcache em um editor de texto.
1. Localizar `opcache.save_comments` e remova o comentário, se necessário.
1. Verifique se o valor está definido como `1`.
1. Salve as alterações e saia do editor de texto.
1. Reiniciar o servidor Web:

   * Apache, Ubuntu: `service apache2 restart`
   * Apache, CentOS: `service httpd restart`
   * nginx, Ubuntu e CentOS: `service nginx restart`

1. Gerar novamente a configuração de ID e todas as classes ausentes que podem ser geradas automaticamente:

```bash
    $ bin/magento setup:di:compile`
```
