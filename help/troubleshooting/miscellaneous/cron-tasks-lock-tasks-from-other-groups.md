---
title: Cron tarefas bloqueiam tarefas de outros grupos
description: Este artigo fornece uma solução para o problema de infraestrutura em nuvem do Adobe Commerce relacionado a determinados trabalhos cron de longa duração que bloqueiam outros trabalhos cron.
exl-id: b5b9e8b3-373c-4f93-af9c-85da84dbc928
feature: Configuration
role: Developer
source-git-commit: faa80e8233438fc15781341b3a9d5325269d6d20
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 0%

---

# Cron tarefas bloqueiam tarefas de outros grupos

Este artigo fornece uma solução para o problema de infraestrutura em nuvem do Adobe Commerce relacionado a determinados trabalhos cron de longa duração que bloqueiam outros trabalhos cron.

## Produtos e versões afetados

* Arquitetura do plano Pro da infraestrutura em nuvem do Adobe Commerce
* Integrado antes de maio de 2019

## Problema

No Adobe Commerce para nuvem, quando você tem tarefas cron complexas (tarefas de longa duração), elas podem bloquear outras tarefas para execução. Por exemplo, a tarefa dos indexadores reindexa os indexadores invalidados. Pode levar algumas horas para ser concluído e bloqueará outros trabalhos cron padrão, como enviar emails, gerar mapas de site, notificações de clientes e outras tarefas personalizadas.

<u>Sintomas</u>:

Os processos executados pelos trabalhos cron não são executados. Por exemplo, as atualizações de produtos não são aplicadas por horas ou os clientes relatam não receber emails.

Ao abrir a tabela de banco de dados `cron_schedule`, você verá os trabalhos com o status `missed`.

## Causa

Anteriormente, em nosso ambiente de nuvem, o servidor Jenkins era usado para executar trabalhos cron. O Jenkins executará somente uma instância de um trabalho por vez; consequentemente, haverá somente um processo `bin/magento cron:run` em execução por vez.

## Solução

1. Contate o [suporte da Adobe Commerce](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) para habilitar os crons autogerenciados.
1. Edite o arquivo `.magento.app.yaml` no diretório raiz do código do Adobe Commerce na ramificação Git. Adicione o seguinte:

   ```yaml
     crons:
     cronrun:
     spec: "* * * * *"
     cmd: "php bin/magento cron:run"
   ```

1. Salve o arquivo e envie as atualizações para os ambientes de preparo e produção (da mesma forma que faz para os ambientes de integração).

>[!NOTE]
>
>Não há necessidade de transferir configurações cron antigas em que vários `cron:run` estão presentes para o novo cronograma cron. A tarefa `cron:run` normal, adicionada conforme descrito acima, é suficiente. No entanto, é necessário transferir seus trabalhos personalizados, se você tiver algum.

### Verifique se você tem o cron gerenciado automaticamente habilitado (somente para Preparo e Produção do Cloud Pro)

Para verificar se o cron autogerenciado está habilitado, execute o comando `crontab -l` e observe o resultado:

* O cron autogerenciado será ativado se você conseguir ver as tarefas, como as seguintes:

  ```bash
  username@hostname:~$ crontab -l    # Crontab is managed by the system, attempts to edit it directly will fail.
  SHELL=/etc/platform/username/cron-run    MAILTO=""    # m h dom mon dow job_name    * * * * * cronrun
  ```

* O cron autogerenciado não é habilitado se você não puder ver as tarefas e obter a mensagem de erro *&quot;você não tem permissão para usar este programa&quot;*.

>[!NOTE]
>
>O comando mencionado acima para verificar se o cron autogerenciado está habilitado não se aplica a um plano inicial e no ambiente de desenvolvimento/integração.

## Leitura relacionada

* [Configure os trabalhos cron](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs) em nossa documentação do desenvolvedor.
