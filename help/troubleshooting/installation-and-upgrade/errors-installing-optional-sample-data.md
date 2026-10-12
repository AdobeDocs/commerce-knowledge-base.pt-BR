---
title: Erros ao instalar dados de amostra opcionais
description: Este tópico discute soluções para erros que você pode encontrar ao instalar dados de amostra opcionais.
exl-id: 14692e3a-188c-45f1-9df5-ac873cc9eff0
feature: Console, Install, Upgrade
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 6388cf7b-8a81-5248-a1e4-7bb57bbe250f
    internal-label: Install
  - id: a8ae7a5a-6cdc-5922-bd0d-6feb44b04984
    internal-label: Upgrade
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
subfeature_v2:
  - id: c4af0798-d497-5e6b-8380-19812c26d00a
    internal-label: Console
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '417'
ht-degree: 0%
---
# Erros ao instalar dados de amostra opcionais

Este tópico discute soluções para erros que você pode encontrar ao instalar dados de amostra opcionais.

## Sintoma (permissões do sistema de arquivos)

Erro no log do console durante a instalação de dados de exemplo usando o Assistente de Instalação:

```php
Module 'Magento_CatalogRuleSampleData':
[ERROR] exception 'Magento\Framework\Exception\LocalizedException' with message 'Can't create directory /var/www/html/magento2/generated/code/Magento/CatalogRule/Model/.' in /var/www/html/magento2/lib/internal/Magento/Framework/Code/Generator.php:103

(more)

Next exception 'ReflectionException' with message 'Class Magento\CatalogRule\Model\RuleFactory does not exist' in /var/www/html/magento2/lib/internal/Magento/Framework/Code/Reader/ClassReader.php:29

(more)
```

Essas exceções resultam das configurações de permissões do sistema de arquivos.

### Solução

[Defina novamente a propriedade e as permissões do sistema de arquivos](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/file-system-permissions.html) como um usuário com `root` privilégios.

## Sintoma (modo de produção)

Se você estiver definido atualmente para [modo de produção](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/setup/application-modes.html), a instalação de dados de amostra falhará se você usar o comando [magento sampledata:deploy](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/next-steps/sample-data/composer-packages.html):

```php
PHP Fatal error: Uncaught TypeError: Argument 1 passed to Symfony\Component\Console\Input\ArrayInput::__construct() must be of the type array, object given, called in /<path>/vendor/magento/framework/ObjectManager/Factory/AbstractFactory.php on line 97 and defined in /<path>/vendor/symfony/console/Symfony/Component/Console/Input/ArrayInput.php:37
```

### Solução

Não instale dados de amostra no modo de produção. Alterne para o modo de desenvolvedor, limpe alguns diretórios `var` e tente novamente.

Digite os seguintes comandos na ordem mostrada como o [proprietário do sistema de arquivos do Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/prerequisites/file-system/overview.html):

```php
cd <magento_root>
bin/magento deploy:mode:set developer
rm -rf generated/code/* generated/metadata/*
bin/magento sampledata:deploy
```

## Sintoma (segurança)

Durante a instalação de dados de amostra opcionais, uma mensagem semelhante à seguinte é exibida:

```php
PHP Fatal error: Call to undefined method Magento\Catalog\Model\Resource\Product\Interceptor::getWriteConnection() in /var/www/magento2/app/code/Magento/SampleData/Module/Catalog/Setup/Product/Gallery.php on line 144
```

### Solução

Durante a instalação dos dados de amostra, desative o SELinux usando um recurso como:

* [www.ibm.com](https://www.ibm.com/docs/ja/ahts/4.0?topic=t-disabling-selinux)
* [Documentação do CentOS](https://docs.centos.org/en-US/docs/)

## Sintoma (desenvolver ramificação)

Outros erros são exibidos, como:

```php
[Magento\Setup\SampleDataException] Error during sample data installation: Class Magento\Sales\Model\Service\OrderFactory does not exist
```

### Solução

Há problemas conhecidos no uso de dados de amostra com a ramificação de desenvolvimento do Adobe Commerce. Em vez disso, use a ramificação mestre. Você pode alternar para a ramificação mestre da seguinte maneira:

```php
cd <magento_root>
git checkout master
git pull origin master
```

## Sintoma (max_execution_time)

A instalação é interrompida antes que a instalação de dados de amostra seja concluída. Um exemplo é o seguinte:

```php
(more)

Module 'Magento_CustomerSampleData':
Installing data...
```

A instalação de dados de exemplo não termina.

Este erro ocorre quando o tempo máximo de execução configurado de seus scripts PHP é excedido. Como os dados de amostra podem levar muito tempo para serem carregados, você pode aumentar o valor durante a instalação.

### Solução

Como um usuário com privilégios `root`, modifique `php.ini` para aumentar o valor de `max_execution_time` para 600 ou mais. (600 segundos são 10 minutos. Você pode aumentar o valor para o valor que desejar.) Você deve alterar `max_execution_time` de volta para seu valor anterior após a instalação ser bem-sucedida.

Se você não tiver certeza de onde `php.ini` está localizado, digite o seguinte comando:

```php
php --ini
```

O valor de `Loaded Configuration File` é o `php.ini` que você deve modificar.

>[!NOTE]
>
>Estamos cientes de que este artigo ainda pode conter termos de software padrão da indústria que alguns podem achar racistas, sexistas ou opressivos e que podem fazer com que o leitor se sinta ferido, traumatizado ou indesejado. O Adobe está trabalhando para remover esses termos de nosso código, documentação e experiências do usuário.
