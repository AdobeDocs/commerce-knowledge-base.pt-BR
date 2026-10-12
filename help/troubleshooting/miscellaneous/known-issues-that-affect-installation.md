---
title: Problemas conhecidos que afetam a instalação do xdebug
description: Este artigo fornece uma solução para quando ocorrer um erro de exceção ao usar a extensão opcional do PHP "xdebug".
exl-id: 5090ea99-e0c3-436a-809b-109701740927
feature: Install
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 6388cf7b-8a81-5248-a1e4-7bb57bbe250f
    internal-label: Install
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '109'
ht-degree: 0%
---
# Problemas conhecidos que afetam a instalação do xdebug

Este artigo fornece uma solução para quando ocorrer um erro de exceção ao usar a extensão opcional do PHP `xdebug`.

* Durante a instalação
* Acessar o administrador ou a loja da Commerce após uma instalação bem-sucedida

Exemplo de exceção:

```php
Fatal error: Maximum function nesting level of '100' reached, aborting!
```

Para resolver esse problema, você pode:

* Desabilite a extensão `xdebug`.
* Defina o valor de `xdebug.max_nesting_level` com um valor de 200 ou mais. Para obter mais informações, consulte [xdebug documentation](http://xdebug.org/docs/basic#max_nesting_level).

Depois de alterar a configuração de ou desabilitar o `xdebug`, reinicie o Apache:

* CentOS: `sudo service httpd restart`
* Ubuntu: `sudo service apache2 restart`
