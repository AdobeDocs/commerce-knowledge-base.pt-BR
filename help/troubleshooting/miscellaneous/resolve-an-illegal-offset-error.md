---
title: Resolver um erro de deslocamento ilegal
description: Este artigo fornece uma solução para quando, no Adobe Commerce 2.1 ou posterior, você recebe um erro Resolver um deslocamento ilegal ao criar um novo produto no Administrador do Commerce.
exl-id: 62d16d3c-7f4b-45e9-ae4b-fe2b58cc3620
feature: Configuration
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '324'
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

O Adobe Commerce 2.1 e versões posteriores usam comentários de código PHP na chamada de validação `getDocComment` no método [`getExtensionAttributes`](https://github.com/magento/magento2/blob/2.3/lib/internal/Magento/Framework/Api/ExtensionAttributesFactory.php#L64-L73) em `Magento\Framework\Api\ExtensionAttributesFactory.php`.

Se você habilitou o OPcache do PHP (o que recomendamos), este erro é exibido porque, por padrão, a configuração do OPcache [`opcache.save_comments`](http://php.net/manual/en/opcache.configuration.php#ini.opcache.save_comments) está desabilitada.

## Solução alternativa

Para resolver o problema, localize suas definições de configuração do OPcache e habilite o `opcache.save_comments` da seguinte maneira:

### Etapa 1: Localizar a configuração do OPcache

#### Para localizar as definições de configuração do OPcache:

Normalmente, as configurações de OPcache do PHP estão localizadas em `php.ini` ou `opcache.ini`. A localização pode depender do seu sistema operacional e da versão do PHP. O arquivo de configuração OPcache pode ter uma seção `[opcache]` ou configurações como `opcache.enable`.

Use as diretrizes a seguir para encontrá-la:

* Apache Web Server:<br>

Para o Ubuntu com Apache, as configurações do OPcache normalmente estão localizadas em `php.ini`.<br>
Para CentOS com Apache ou nginx, as configurações de OPcache normalmente estão localizadas em `/etc/php.d/opcache.ini`.<br>
Caso contrário, use o seguinte comando para localizá-lo:

```bash
    $ sudo find / -name 'opcache.ini'
```

* servidor Web nginx com PHP-FPM: `/etc/php5/fpm/php.ini`.

Se você tiver mais de um `opcache.ini`, modifique todos eles.


### Etapa 2: Habilitar `opcache.save_comments`

1. Abra o arquivo de configuração do OPcache em um editor de texto.
1. Localize `opcache.save_comments` e remova o comentário, se necessário.
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
