---
title: A "Magento-cloud" [!DNL CLI] não mostra um ambiente ativo
description: Este artigo descreve um problema conhecido do Adobe Commerce em que a "Magento-cloud" [!DNL CLI] (ferramenta de linha de comando) não mostra um ambiente ativo.
feature: Cloud, Integration, Configuration
role: Developer
exl-id: 3c1b5de2-8888-4531-9dc1-cd478e3c96fc
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 5a951749-fac9-5bc7-9a98-ebe4ff066437
    internal-label: Cloud
  - id: cc04bd17-78d5-5120-8c3d-1b8a57e49280
    internal-label: Integration
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '136'
ht-degree: 0%
---
# O `Magento-cloud` [!DNL CLI] não mostra um ambiente ativo

## Problema

Existem vários ambientes ativos e você está tentando interagir com um ambiente executando um comando `Magento-cloud` [!DNL CLI] (ferramenta de linha de comando). (Por exemplo: `ssh`, `db:size`, `db:sql`, etc.)
No entanto, o prompt para escolher o ambiente desejado não lista esse ambiente. (Por exemplo: o ambiente de integração)

```
Enter a number to choose an environment:
Default: master
  [0] integration2 (type: development)
  [1] master (type: development)
  [2] production
  [3] staging
 >
```

## Causa

O ambiente pode não estar disponível devido a uma implantação que está em andamento, travada ou que falhou.

## Solução

Será necessário especificar manualmente o ambiente com o sinalizador `e|-environment`.

1. Encontre a lista de ambientes ativos e anote os nomes dos ambientes:

```
$ magento-cloud environment: list |grep "Active\|ID"
Your environments are:

| ID                     | Title            | Status       | Type           |
| Master                 | Master           | Active       | Development    |
|   Production           | Production       | Active       | Production     |
|     Staging            | Staging          | Active       | Staging        |
|       Integration      | Integration      | Active       | Development    |
|          Integration 2 | Integration 2    | Active       | Development    |
```

&#x200B;2. Especifique a ID do ambiente com seu comando:

`magento-cloud ssh -e integration`
