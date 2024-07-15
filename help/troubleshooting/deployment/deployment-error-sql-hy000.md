---
title: "Erro de implantação: SQLSTATE[HY000]"
description: Este artigo fornece uma solução para o problema em que a implantação falha devido ao erro SQLSTATE[HY000].
exl-id: c6da6275-9327-4a5c-99ed-93a53952ba42
feature: Deploy
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '83'
ht-degree: 0%

---

# Erro de implantação: SQLSTATE[HY000]

Este artigo fornece uma solução para o problema em que a implantação falha devido ao erro SQLSTATE[HY000].

## Produtos e versões afetados

* Adobe Commerce, [todos os métodos de implantação](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Problema

Ocorre um erro SQLSTATE durante a implantação.

```sql
Updating modules:
SQLSTATE[HY000]: General error: 23 Out of resources when opening file '/tmp/#sql_565c_0.MAD' (Errcode: 24 "Too many open files"),
```

## Causa

Cron em execução durante a implantação.

## Solução

Para resolver o problema, pare a execução do cron abrindo a linha de comando e executando o seguinte comando:
`./vendor/bin/ece-tools cron:disable`.
