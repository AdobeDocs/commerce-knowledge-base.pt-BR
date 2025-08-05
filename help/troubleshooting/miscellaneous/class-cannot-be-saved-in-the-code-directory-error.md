---
title: Erro "A classe não pode ser salva no diretório de código"
description: Este artigo descreve como corrigir o problema em que a maneira como você especificou dependências impede que as classes sejam geradas automaticamente em tempo real, e você recebe a mensagem de erro *"A classe não pode ser salva no diretório gerado/de código"*.
exl-id: e2c00d4d-31c3-4446-a317-a8ac92c707d5
feature: Configuration
role: Developer
source-git-commit: 139c2836ba36686357c7a5458a36550c7b1273c1
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---

# Erro &quot;A classe não pode ser salva no diretório de código&quot;

Este artigo descreve como corrigir o problema em que a maneira como você especificou dependências impede que as classes sejam geradas automaticamente em tempo real, e você recebe a mensagem de erro *&quot;A classe não pode ser salva no diretório gerada/código&quot;*.

## Produtos e versões afetados

* Adobe Commerce na infraestrutura em nuvem 2.2.0 ou posterior

## Problema

<u>Etapas a serem reproduzidas</u>

1. No ambiente local, escreva uma classe personalizada com uma dependência na classe gerada automaticamente.
1. Execute o cenário em que sua classe personalizada é acionada e veja se ela funciona corretamente.
1. Confirme e envie suas alterações para o ambiente de integração. Isso acionaria o processo de implantação. Implantação bem-sucedida.
1. No [ambiente de integração](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-27242), execute o cenário em que sua classe personalizada é acionada.

<u>Resultado esperado</u>

Tudo funciona corretamente, da mesma forma que no seu ambiente local.

<u>Resultado real</u>

Falha com a mensagem de erro informando que a classe não pode ser salva no diretório `generated/code`.

## Causa

A causa do problema é que a classe na qual você tem dependência, não é gerada durante a implantação e não pode ser gerada posteriormente quando a classe é acionada, pois o diretório `generated/code` não está disponível para gravação após a implantação ser concluída.

Há duas razões principais pelas quais isso pode acontecer:

* Caso 1: A classe com dependências em classes geradas automaticamente está localizada no ponto de entrada (como `index.php` ), que não é verificado em busca de dependências durante a implantação.
* Caso 2: a dependência da classe gerada automaticamente é especificada diretamente (compare com o uso recomendado do construtor para declarar dependência).

## Solução

Uma solução comum para ambos os casos seria criar uma fábrica real em vez da classe gerada automaticamente.

Ou há uma solução específica para cada caso.

### Solução específica para o caso 1

Mova seu código de classe do ponto de entrada para um módulo separado e use-o no ponto de entrada.

<u>Exemplo</u>

Código original em, por exemplo, `index2.php`:

```php
<?php
use YourVendor\SomeModule\Model\GeneratedFactory;

require realpath(__DIR__) . '/../app/bootstrap.php';
$bootstrap = \Magento\Framework\App\Bootstrap::create(BP, $_SERVER);

class SomeClass
{
    private $generatedFactory;

    public function __construct(GeneratedFactory $generatedFactory)
    {
        $this->generatedFactory = $generatedFactory;
    }

// Some code here...
}

$someObject = $bootstrap->getObjectManager()->create(SomeClass::class);

// There is some code that uses $someObject
```

Você precisa executar as seguintes etapas:

1. Mover a definição de classe para `app/code/YourVendor/YourModule`:

   ```php
      <?php
       namespace YourVendor\YourModule;
       use YourVendor\YourModule\Model\GeneratedFactory;
       class YourClass
       {
           private $generatedFactory;
   
           public function __construct(GeneratedFactory $generatedFactory)
           {
               $this->generatedFactory = $generatedFactory;
           }
       // Some code here...
       }
   ```

1. Edite o ponto de entrada `my_api/index.php` de forma que ele tenha a seguinte aparência:

   ```php
     <?php
     use YourVendor\YourModule\YourClass;
         require realpath(__DIR__) . '/../app/bootstrap.php';
         $bootstrap = \Magento\Framework\App\Bootstrap::create(BP, $_SERVER);
         $someObject = $bootstrap->getObjectManager()->create(YourClass::class);
     // Some code using $someObject
   ```

### Solução específica para o caso 2

Mova a declaração de dependência para o construtor.

<u>Exemplo</u>

Declaração de classe original:

```php
<?php
namespace YourVendor\YourModule;

use YourVendor\SomeModule\Model\GeneratedFactory;
use Magento\Framework\App\ObjectManager;

class YourClass
{
    private $generatedFactory;
    private $someParam;

    public function __construct($someParam)
    {
        $this--->someParam = $someParam;
        $this->generatedFactory = ObjectManager::getInstance()->get(GeneratedFactory::class);
    }

    // Some code here...
}
```

Você precisa alterar seu construtor da seguinte maneira:

```php
<?php
namespace YourVendor\YourModule;

use YourVendor\YourModule\Model\GeneratedFactory;
use Magento\Framework\App\ObjectManager;

class YourClass
{
    private $generatedFactory;
    private $someParam;

    public function __construct($someParam, GeneratedFactory $generatedFactory = null)
    {
        $this->someParam = $someParam;
        $this->generatedFactory = $generatedFactory ?: ObjectManager::getInstance()->get(GeneratedFactory::class);
    }

    // Some code here...
}
```

## Leitura relacionada

* [Geração de código](https://developer.adobe.com/commerce/php/development/components/code-generation/) em nossa documentação para desenvolvedores.
