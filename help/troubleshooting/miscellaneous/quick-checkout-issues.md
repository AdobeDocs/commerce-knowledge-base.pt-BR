---
title: Solução de problemas de Check-out rápido
description: Este artigo explica problemas que você pode ter ao usar a extensão Quick Checkout for Adobe Commerce e fornece soluções para corrigir esses problemas para que você possa usar a extensão com êxito.
exl-id: 8ab46318-d62a-4b7e-bbe5-4c52cfeb9e36
feature: Checkout, Orders
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# Solução de problemas de Check-out rápido

Este artigo explica problemas que você pode ter ao usar a extensão Quick Checkout for Adobe Commerce e fornece soluções para corrigir esses problemas para que você possa usar a extensão com êxito.

## Produtos e versões afetados

* A variável [Check-out rápido](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/overview.html) O é compatível com o Magento Open Source e o Adobe Commerce. Consulte [Política de ciclo de vida](https://experienceleague.adobe.com/docs/commerce-operations/release/planning/lifecycle-policy.html) para obter mais informações sobre as versões compatíveis.

## Chaves do Composer incorretas e estabilidade mínima para `RC`

<u>Causa</u>:

Se você vir a seguinte mensagem de erro, você pode ter chaves de compositor incorretas:

```terminal
Could not find a matching version of package magento/quick-checkout. Check the package spelling, your version constraint and that the package is available in a stability which matches your minimum-stability (RC).
```

<u>Solução</u>:

Verifique se as teclas do compositor estão vinculadas ao _ID do Magento_ usado durante o registro do Check-out rápido.

Para ver quais teclas do compositor estão configuradas:

1. Localize o `auth.json` arquivo:

   ```bash
   composer config --global home
   ```

1. Exibir o `auth.json` arquivo:

   ```bash
   cat /path/to/auth.json
   ```

1. Consulte [quais chaves estão associadas à sua ID de Magento](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html).

1. Defina a estabilidade mínima como `RC` no `composer.json` arquivo.

   ```json
   "minimum-stability": "RC"
   ```

## Memória insuficiente para o PHP

<u>Causa</u>:

Se você vir a seguinte mensagem de erro indicando que você não tem memória suficiente para o PHP:

```terminal
Fatal error: Allowed memory size of 2146435072 bytes exhausted (tried to allocate 4096 bytes) in phar:///usr/local/bin/composer/src/Composer/DependencyResolver/RuleWatchGraph.php on line 52
```

<u>Solução</u>:

[Aumente o limite de memória](https://devdocs.magento.com/cloud/project/magento-app-php-ini.html#increase-php-memory-limit) para PHP em seu ambiente no `php.ini`.

Como alternativa, você pode especificar o limite de memória usando este comando: `php -d memory_limit=-1 [path to composer]/composer require magento/quick-checkout`.

Por exemplo:

```bash
php -d memory_limit=-1 vendor/bin/composer require magento/quick-checkout
```

## Adicionar linhas de endereço com um novo endereço de entrega

Há um problema conhecido para a extensão Check-out rápido.

Quando você [fazer logon com uma conta do Bolt](https://help.bolt.com/shoppers/guides/checkout/log-in/), é possível adicionar um novo endereço de entrega com uma limitação de 4 linhas por endereço.

Se o novo endereço de entrega contiver mais de 4 linhas, elas não serão armazenadas.

O Adobe Commerce geralmente pode ser configurado para oferecer suporte a até 20 linhas de endereço.

## Comportamento inesperado quando `Display Billing Address On` está definida como `payment page`

Há um problema conhecido para a extensão Check-out rápido.

Se você definir a variável `Display Billing Address On` parâmetro para o `payment page` e [fazer logon com uma conta do Bolt](https://help.bolt.com/shoppers/guides/checkout/log-in/) ao marcar a opção `My billing and shipping address are the same` caixa de seleção, o botão de opção é exibido `use existing card`. Como o endereço de cobrança só é aplicável para novos cartões de crédito, o endereço não estará visível até que o usuário do Bolt decida adicionar uma nova opção de cartão de crédito.

Consulte a [Check-out](https://docs.magento.com/user-guide/configuration/sales/checkout.html) tópico para obter mais informações sobre a `Display Billing Address On` parâmetro.
