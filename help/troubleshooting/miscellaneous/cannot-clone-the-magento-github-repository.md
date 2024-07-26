---
title: Não é possível clonar o repositório GitHub do Magento
description: Este artigo fornece uma correção para quando não é possível clonar o repositório GitHub do Magento.
exl-id: 65de77b5-496d-42a3-ab2e-1fff9df97160
feature: Data Import/Export
role: Developer
source-git-commit: 35d4f2130d0ec71f71f5f20aa8a7c76207e7a35a
workflow-type: tm+mt
source-wordcount: '62'
ht-degree: 0%

---

# Não é possível clonar o repositório GitHub do Magento

Este artigo fornece uma correção para quando não é possível clonar o repositório GitHub do Magento.

## Detalhe {#detail}

O erro é semelhante ao seguinte:

```bash
Cloning into 'magento2'...
Permission denied (publickey).
fatal: The remote end hung up unexpectedly
```

## Solução {#solution}

Carregue sua chave SSH no GitHub conforme discutido em [a página de ajuda do GitHub](https://help.github.com/articles/generating-ssh-keys).
