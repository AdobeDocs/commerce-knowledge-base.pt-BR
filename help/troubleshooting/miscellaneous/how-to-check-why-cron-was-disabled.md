---
title: Como verificar por que  [!DNL cron]  foi desabilitado
description: Este artigo oferece soluções de problemas com o cron na Adobe Commerce em produtos de infraestrutura em nuvem.
feature: Configuration
role: Developer
exl-id: d4d4a28d-3afa-4379-afc1-bc6250717784
source-git-commit: c5e94c6407394cd905ea470628d28db2c2c6c0ed
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 0%

---

# Como verificar por que [!DNL cron] foi desabilitado

Este artigo oferece soluções de problemas com o [!DNL cron] nos produtos Adobe Commerce on cloud infrastructure.

## Produtos e versões afetados

* Adobe Commerce na infraestrutura em nuvem, todas as versões

## Problema

## Estes são os sintomas de [!DNL cron] problemas:

Você notou que o [!DNL cron] não estava em execução.
Por exemplo: você vê as seguintes linhas no arquivo `app/etc/env.php`:

```'cron' =>
  array (
    'enabled' => 0
  ),
```

Uma matriz vazia significaria que [!DNL cron] está **habilitado**:

```'cron' =>
  array (
  ),
```

## Causas

Há vários motivos pelos quais o [!DNL cron] não está ativo no momento:

1. O [!DNL cron] foi desabilitado devido a configurações [!DNL OpCache] ausentes.
1. A equipe de Infraestrutura desabilitou [!DNL cron] porque estava causando mau desempenho/inatividade no site.
1. O [!DNL cron] não foi reabilitado porque sua implantação falhou.

Consulte uma das seções a seguir para obter uma solução para o seu problema.

## Soluções

### Solução para configurações perdidas [!DNL OpCache] {#solution-missed-opcache-settings}

Consulte [[!DNL Cron] interrompido devido a configurações incorretas ou ausentes [!DNL OpCache] configurações](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/crons-blocked-running-missing-opache-settings) em nossa base de dados de conhecimento Commerce.

### Solução para desabilitados pela equipe de infraestrutura {#solution-disabled-by-infrastructure-team}

1. Verifique os tíquetes de suporte anteriores em que o site estava inativo ou não estava respondendo.
1. Em seguida, verifique se a equipe de infraestrutura indicou que a desativou.
1. Verifique se você solucionou os problemas/preocupações apresentados pela equipe de infraestrutura.
1. Envie uma [Solicitação de suporte](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-tickets) se precisar de mais assistência para solicitar a reativação de [!DNL cron] e explicar como você resolveu os problemas indicados pela equipe de infraestrutura.

### Falha na solução para implantação {#solution-deployment-failed}

Verifique os logs de implantação:

* [Exiba e gerencie logs](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/test/log-locations) em nosso Guia do Commerce na Infraestrutura em Nuvem.
* [Verificando o log de implantação se a Interface do Usuário da Nuvem tem *`log snipped`* erro](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/checking-deployment-log-if-the-cloud-ui-shows-log-snipped-error) em nossa Base de Dados de Conhecimento Commerce.

1. Se a implantação falhou durante a etapa `setup:upgrade`, o [!DNL cron] não terá sido reativado.
Por exemplo: você verá esta linha no log de implantação:

   ```The command "/bin/bash -c "set -o pipefail; php ./bin/magento setup:upgrade --keep-generated --ansi --no-interaction  | tee -a /app/$<project_id>/var/log/install_upgrade.log"" failed. Cache types config flushed successfully```

1. Caso contrário, a implantação pode ter falhado durante algum outro estágio. Verifique o log de implantação e verifique se ambas as linhas são exibidas (exemplo abaixo). Se você não vir ambas as linhas semelhantes a esta no log, significa que o [!DNL cron] não foi reativado:

   ```  [2024-03-06T10:55:39.345564+00:00] INFO: Disable cron```<br>
...<br>
   ```  [2024-02-07T10:50:09.579005+00:00] INFO: Enable cron```

**Envie uma [Solicitação de suporte](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-tickets) se precisar de mais ajuda.**
