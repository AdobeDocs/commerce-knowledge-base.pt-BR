---
title: Problemas conhecidos que afetam a instalação do xdebug
description: Este artigo fornece uma solução para quando ocorrer um erro de exceção ao usar a extensão opcional do PHP "xdebug".
exl-id: 5090ea99-e0c3-436a-809b-109701740927
feature: Install
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '105'
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

* Desative o `xdebug` extensão.
* Defina o valor de `xdebug.max_nesting_level` para um valor de 200 ou mais. Para obter mais informações, consulte [documentação do xdebug](http://xdebug.org/docs/basic#max_nesting_level).

Depois de alterar a configuração de ou desativar o `xdebug`, reinicie o Apache:

* CentOS: `sudo service httpd restart`
* Ubuntu: `sudo service apache2 restart`
