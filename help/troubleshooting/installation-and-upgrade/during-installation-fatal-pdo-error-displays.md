---
title: Durante a instalação, um erro fatal de PDO é exibido
description: Este artigo fornece uma correção para um erro fatal de PDO de exceção durante a instalação.
exl-id: d69908f0-71c9-48de-9369-6ada22f2b393
feature: Install, Upgrade
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '50'
ht-degree: 0%

---

# Durante a instalação, um erro fatal de PDO é exibido

Este artigo fornece uma correção para um erro fatal de PDO de exceção durante a instalação.

## Problema

```php
PHP Fatal error:  Class 'PDO' not found in /var/www/html/magento2/setup/module/Magento/Setup/src/Module/Setup/ConnectionFactory.php on line 44
```

## Solução

Certifique-se de instalar todas as [extensões PHP necessárias](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/installation-guide/prerequisites/php-settings).
