---
title: 'Erro de implantação: SQLSTATE[HY000]'
description: Este artigo fornece uma solução para o problema em que a implantação falha devido ao erro SQLSTATE[HY000].
exl-id: c6da6275-9327-4a5c-99ed-93a53952ba42
feature: Deploy
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: bcd8874c-7b93-5596-bdaa-22660e84df14
    internal-label: Deploy
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '94'
ht-degree: 5%
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
