---
title: Durante a instalação, um erro fatal de PDO é exibido
description: Este artigo fornece uma correção para um erro fatal de PDO de exceção durante a instalação.
exl-id: d69908f0-71c9-48de-9369-6ada22f2b393
feature: Install, Upgrade
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 6388cf7b-8a81-5248-a1e4-7bb57bbe250f
    internal-label: Install
  - id: a8ae7a5a-6cdc-5922-bd0d-6feb44b04984
    internal-label: Upgrade
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '60'
ht-degree: 0%
---
# Durante a instalação, um erro fatal de PDO é exibido

Este artigo fornece uma correção para um erro fatal de PDO de exceção durante a instalação.

## Problema

```php
PHP Fatal error:  Class 'PDO' not found in /var/www/html/magento2/setup/module/Magento/Setup/src/Module/Setup/ConnectionFactory.php on line 44
```

## Solução

Certifique-se de instalar todas as [extensões PHP necessárias](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/php-settings).
