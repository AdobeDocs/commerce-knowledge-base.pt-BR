---
title: Como verificar o motivo [!DNL cron] foi desabilitado
description: Este artigo oferece soluções de problemas com o cron na Adobe Commerce em produtos de infraestrutura em nuvem.
feature: Configuration
role: Developer
exl-id: d4d4a28d-3afa-4379-afc1-bc6250717784
source-git-commit: c5e94c6407394cd905ea470628d28db2c2c6c0ed
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 0%

---

# Como verificar o motivo [!DNL cron] foi desabilitado

Este artigo oferece soluções de problemas com [!DNL cron] em produtos de infraestrutura em nuvem do Adobe Commerce.

## Produtos e versões afetados

* Adobe Commerce na infraestrutura em nuvem, todas as versões

## Problema

## A seguir estão os sintomas de [!DNL cron] problemas:

Você notou que o seu [!DNL cron] não estava correndo.
Por exemplo: você vê as seguintes linhas no `app/etc/env.php` arquivo:

```'cron' =>
  array (
    'enabled' => 0
  ),
```

Uma matriz vazia significaria que a variável [!DNL cron] é **habilitado**:

```'cron' =>
  array (
  ),
```

## Causas

Existem várias razões pelas quais a [!DNL cron] não está ativo no momento:

1. A variável [!DNL cron] foi desativado devido a erro [!DNL OpCache] configurações.
1. A equipe de infraestrutura desativou seu [!DNL cron], pois estava causando um desempenho insatisfatório/inativo no site.
1. A variável [!DNL cron] não foi reabilitado porque sua implantação falhou.

Consulte uma das seções a seguir para obter uma solução para o seu problema.

## Soluções

### Solução para perdido [!DNL OpCache] configurações {#solution-missed-opcache-settings}

Consulte [[!DNL Cron] interrompido devido a uma configuração incorreta ou ausente [!DNL OpCache] configurações](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/crons-blocked-running-missing-opache-settings) na nossa base de conhecimento Commerce.

### Solução para desabilitados pela equipe de infraestrutura {#solution-disabled-by-infrastructure-team}

1. Verifique os tíquetes de suporte anteriores em que o site estava inativo ou não estava respondendo.
1. Em seguida, verifique se a equipe de infraestrutura indicou que a desativou.
1. Verifique se você solucionou os problemas/preocupações apresentados pela equipe de infraestrutura.
1. Enviar um [Solicitação de suporte](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-tickets) se precisar de mais assistência para solicitar a reativação do [!DNL cron] e explique como você abordou os problemas indicados pela equipe de infraestrutura.

### Falha na solução para implantação {#solution-deployment-failed}

Verifique os logs de implantação:

* [Exibir e gerenciar logs](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/test/log-locations) em nosso Guia de infraestrutura do Commerce na nuvem.
* [Verificação do log de implantação se a interface do Cloud tem *`log snipped`* erro](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/checking-deployment-log-if-the-cloud-ui-shows-log-snipped-error) na nossa base de conhecimento Commerce.

1. Se a implantação tiver falhado durante `setup:upgrade` etapa, a variável [!DNL cron] não terá sido reativada.
Por exemplo: você verá esta linha no log de implantação:

   ```The command "/bin/bash -c "set -o pipefail; php ./bin/magento setup:upgrade --keep-generated --ansi --no-interaction  | tee -a /app/$<project_id>/var/log/install_upgrade.log"" failed. Cache types config flushed successfully```

1. Caso contrário, a implantação pode ter falhado durante algum outro estágio. Verifique o log de implantação e verifique se ambas as linhas são exibidas (exemplo abaixo). Se você não vir ambas as linhas semelhantes a esta no log, significa que a variável [!DNL cron] não foi reativado:

   ```  [2024-03-06T10:55:39.345564+00:00] INFO: Disable cron```<br>
..<br>
   ```  [2024-02-07T10:50:09.579005+00:00] INFO: Enable cron```

**Enviar um [Solicitação de suporte](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-tickets) se precisar de mais assistência.**
