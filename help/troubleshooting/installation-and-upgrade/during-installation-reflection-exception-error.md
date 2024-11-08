---
title: Durante a instalação, erro de exceção de reflexão
description: Este artigo fornece uma solução para o erro de Exceção de reflexão durante a instalação.
exl-id: aed5f297-1339-4171-9392-04b3f93277ee
feature: Install, Upgrade
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '96'
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
