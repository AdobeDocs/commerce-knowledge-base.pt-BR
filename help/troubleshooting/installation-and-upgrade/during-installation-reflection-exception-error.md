---
title: Durante a instalação, erro de exceção de reflexão
description: Este artigo fornece uma solução para o erro de Exceção de reflexão durante a instalação.
exl-id: aed5f297-1339-4171-9392-04b3f93277ee
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
source-wordcount: '107'
ht-degree: 0%
---
# Durante a instalação, erro de exceção de reflexão

Este artigo fornece uma solução para o erro de Exceção de reflexão durante a instalação.

## Detalhes {#details}

Durante a instalação, uma mensagem semelhante à seguinte é exibida:

```php
[ERROR] exception 'ReflectionException' with message 'Class Magento\Framework\StoreManagerInterface does not exist' in /<path>/lib/internal/Magento/Framework/Code/Reader/ClassReader.php
```

## Solução {#solution}

Limpe todos os diretórios e arquivos no subdiretório `var` da Adobe Commerce e instale o software da Adobe Commerce novamente.

Como o [proprietário do sistema de arquivos do Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/file-system/overview) ou como um usuário com privilégios `root`, insira os seguintes comandos:

```bash
$ cd <your Magento install directory>/var
```

```bash
$ rm -rf var/cache/* di/* generation/* page_cache/*
```

### Redis {#redis}

Se você usar Redis e ainda receber um erro, limpe o cache Redis da seguinte maneira:

```bash
$ redis-cli FLUSHALL
```
