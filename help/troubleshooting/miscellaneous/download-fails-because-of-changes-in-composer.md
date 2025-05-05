---
title: O download falha devido a alterações no Composer
description: Este artigo fornece uma correção para uma falha de download e erro de exceção do Adobe Commerce.
exl-id: 5abdab97-4b0c-466b-a68f-a2637d2826e5
feature: Configuration
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '184'
ht-degree: 0%

---

# O download falha devido a alterações no Composer

Este artigo fornece uma correção para uma falha de download e erro de exceção do Adobe Commerce.

## Problema

Durante o download, o seguinte erro é exibido:

```php
[ErrorException]
  file_get_contents(app/etc/NonComposerComponentRegistration.php): failed to open stream: No such file or directory
```

## Causa

Isso acontece devido a alterações em determinadas versões do Composer. A solução é fazer o downgrade do Composer para uma versão anterior e tentar o download do Adobe Commerce novamente.

## Solução

Qualquer versão do Composer datada de 21 de novembro a 26 de novembro de 2015 tem esse problema. Para confirmar se esse problema está relacionado à versão do Composer, digite o seguinte comando:

```php
composer -v
```

A versão é exibida semelhante ao seguinte:

```php
Composer version 1.0-dev (2b14f0a047dd4f3545ec82381f65c36ea93a4c81) 2015-11-25 17:13:09
```

Observe que a data é 25/11/2015, o que indica que o Composer tem esse problema.

Para contornar isso:

1. Altere sua versão do Composer para permitir que você baixe o software Adobe Commerce seguindo um destes procedimentos:

   * Faça o downgrade do Composer usando o seguinte comando: `composer self-update 1.0.0-alpha11`.
   * Atualize o Composer para uma versão posterior a 26 de novembro de 2015: `composer self-update`.

1. Exclua o diretório e os subdiretórios do Adobe Commerce.
1. Tente baixar novamente usando `[composer create-project](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/installation-guide/composer)` ou `[git clone](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)`.
1. Depois de baixar com êxito o software Adobe Commerce, atualize o Composer: `composer self-update`.
