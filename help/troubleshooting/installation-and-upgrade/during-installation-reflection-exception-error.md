---
title: Durante a instalação, erro de exceção de reflexão
description: Este artigo fornece uma solução para o erro de Exceção de reflexão durante a instalação.
exl-id: aed5f297-1339-4171-9392-04b3f93277ee
feature: Install, Upgrade
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
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

Limpar todos os diretórios e arquivos no Adobe Commerce `var` subdiretório e instale o software Adobe Commerce novamente.

Como a variável [Proprietário do sistema de arquivos Adobe Commerce](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/file-sys-perms-over.html) ou como usuário com `root` insira os seguintes comandos:

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
