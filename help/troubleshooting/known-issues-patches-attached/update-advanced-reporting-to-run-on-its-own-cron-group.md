---
title: Atualizar relatório avançado para executar em seu próprio grupo cron
description: Este artigo fornece uma correção para o problema conhecido do Adobe Commerce na infraestrutura em nuvem 2.3.0, onde os Relatórios avançados não estão mostrando dados. Isso ocorre porque o trabalho de relatório avançado "analytics_collect_data" não é executado de acordo com o agendamento. Este artigo fornece uma correção que criará um grupo cron de Relatórios avançados "analytics".
exl-id: 8aff9e2b-d9be-4136-975b-05963e23f55c
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '275'
ht-degree: 0%

---

# Atualizar relatório avançado para executar em seu próprio grupo cron

Este artigo fornece uma correção para o problema conhecido do Adobe Commerce na infraestrutura em nuvem 2.3.0, onde os Relatórios avançados não estão mostrando dados. Isso ocorre porque o trabalho `analytics_collect_data` do Relatório Avançado não é executado de acordo com o agendamento. Este artigo fornece um patch que criará um grupo cron de Relatórios Avançados `analytics`.

## Problema

Nenhum dado é carregado no módulo de relatórios avançados.

## Correção

O patch está anexado a este artigo. O patch move as tarefas de trabalho `analytics` do cron do grupo padrão para `analytics`.

Para baixá-lo, role para baixo até o final do artigo e clique no nome do arquivo ou clique no link a seguir:

[MDVA-19640\_EE\_2.3.0\_COMPOSER\_v1.patch](assets/MDVA-19640_EE_2.3.0_COMPOSER_v1.patch.zip)

Após aplicar o patch, execute a seguinte consulta SQL. A consulta deve ser executada para alterar registros na tabela `cron_schedule`.

```
UPDATE core_config_data
SET `path` = REPLACE(path, "crontab/default/jobs/analytics", "crontab/analytics/jobs/analytics")
WHERE `path` LIKE "crontab/default/jobs/analytics%";
```

### Versões compatíveis do Adobe Commerce:

A correção foi criada para

* Adobe Commerce na infraestrutura em nuvem 2.3.0

O patch também é compatível (mas pode não resolver o problema) com as seguintes versões e edições do Adobe Commerce: 2.2.2-2.2.10, 2.3.0-2.3.2 e 2.3.2-p2 e 2.3.3, para o Adobe Commerce no local e Adobe Commerce na infraestrutura em nuvem

## Como aplicar o patch

Consulte [Como aplicar um patch de compositor fornecido pelo Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) para obter instruções.

## Arquivos anexados
