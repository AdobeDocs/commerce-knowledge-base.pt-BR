---
title: "[!DNL Cron] a tarefa está paralisada em **status de execução**"
description: Este artigo fornece soluções para quando o Adobe Commerce [!DNL cron] tarefas não terminam de ser executadas e persistem em um status "em execução", o que impede que outras [!DNL cron] tarefas em execução. Isso pode acontecer por vários motivos, como problemas de rede, falhas em aplicativos e problemas de reimplantação.
exl-id: 11e01a2b-2fcf-48c2-871c-08f29cd76250
feature: Configuration
role: Developer
source-git-commit: 08a241131453725a86eda5f267a209e6705da2e3
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---

# [!DNL Cron] a tarefa está paralisada no status &quot;em execução&quot;

Este artigo fornece soluções para quando o Adobe Commerce [!DNL cron] tarefas não terminam de ser executadas e persistem em um status &quot;em execução&quot;, o que impede que outras [!DNL cron] tarefas em execução. Isso pode acontecer por vários motivos, como problemas de rede, falhas em aplicativos e problemas de reimplantação.

## Produtos e versões afetados

Adobe Commerce na infraestrutura em nuvem, todas as versões

## Sintoma {#symptom}

Sintomas de [!DNL cron] os trabalhos que devem ser redefinidos incluem:

* Uma grande quantidade de trabalhos aparece na `cron_schedule` fila
* O desempenho do site começa a diminuir
* Os trabalhos não são executados de acordo com o agendamento

## Soluções {#solutions}

### Solução para interromper todos [!DNL cron] tarefas de uma só vez {#solution-stop-all-crons-at-once}

>[!WARNING]
>
>Executar este comando sem o `--job-code` a opção é redefinida *all* [!DNL cron] tarefas, incluindo aquelas em execução no momento, portanto, recomendamos usá-lo somente em casos excepcionais, como depois de verificar que todas [!DNL cron] os trabalhos devem ser redefinidos. Reimplantação executa este comando por padrão para redefinir [!DNL cron] trabalhos, para que eles se recuperem adequadamente após o backup do ambiente. Evite usar esta solução quando os indexadores estiverem em execução.

Para resolver esse problema, redefina o [!DNL cron] tarefa(s) usando o `cron:unlock` comando. Esse comando altera o status da variável [!DNL cron] job no banco de dados, encerrando o job de forma forçada para permitir que outros jobs agendados continuem.

1. Abra um terminal e use sua [Chaves SSH](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/secure-connections) para conectar-se ao ambiente afetado.
1. Obtenha as credenciais do banco de dados MySQL:    ```shell    echo $MAGENTO_CLOUD_RELATIONSHIPS | base64 -d | json_pp    ```
1. Conectar ao banco de dados usando `mysql` :    ```shell    mysql -hdatabase.internal -uuser -ppassword main    ```
1. Selecione o `main` banco de dados:    ```shell    use main    ```
1. Localizar tudo em execução [!DNL cron] tarefas:    ```shell    SELECT * FROM cron_schedule WHERE status = 'running';    ```
1. Copie o `job_code` de qualquer tarefa que esteja sendo executada por mais tempo do que o normal.
1. Use as IDs de programação da etapa anterior para desbloquear IDs [!DNL cron] tarefas:    ```shell    ./vendor/bin/ece-tools cron:unlock --job-code=<job_code_1> [... --job-code=<job_code_x>]    ```

### Solução para interromper um único [!DNL cron] {#solution-stop-a-single-cron}

1. Abra um terminal e use sua [Chaves SSH](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/secure-connections) para conectar-se ao ambiente afetado.
1. Verifique as tarefas de longa duração usando o seguinte comando:

   ```date; ps aux | grep '[%]CPU\|cron\|magento\|queue' | grep -v 'grep\|cron -f'```

1. Na saída, como na saída de exemplo abaixo, você verá a data atual e a lista de processos. A variável `START` mostra a hora ou data inicial do processo:

   ```
   Wed May  8 22:41:31 UTC 2019
   USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
   root       590  0.0  0.0  27528  2768 ?        Ss   Jan15   0:49 /usr/sbin/cron -f
   bxc2qly+ 25855  0.0  0.0  23724  2184 ?        S    20:51   0:00 logger -d -u /run/bxc2qlykqhbqe_stg-cron.sock -p cron.info -s -t cron-bxc2qlykqhbqe_stg-bxc2qlykqhbqe_stg
   bxc2qly+ 25860 57.7  1.3 584220 222692 ?       S    20:51   0:02 php bin/magento cron:run
   bxc2qly+ 25863  0.0  0.0  23724  2472 ?        S    20:51   0:00 logger -d -u /run/bxc2qlykqhbqe-cron.sock -p cron.info -s -t cron-bxc2qlykqhbqe-bxc2qlykqhbqe
   bxc2qly+ 25876 53.0  0.6 475472 111468 ?       R    20:51   0:01 /usr/bin/php7.1-zts /app/bxc2qlykqhbqe_stg/bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1
   bxc2qly+ 25878 57.0  0.6 475472 112080 ?       R    20:51   0:01 /usr/bin/php7.1-zts /app/bxc2qlykqhbqe_stg/bin/magento cron:run --group=staging --bootstrap=standaloneProcessStarted=1
   bxc2qly+ 25880 50.5  0.6 475472 111312 ?       R    20:51   0:01 /usr/bin/php7.1-zts /app/bxc2qlykqhbqe_stg/bin/magento cron:run --group=catalog_event --bootstrap=standaloneProcessStarted=1
   bxc2qly+ 25882 48.5  0.6 475472 111220 ?       R    20:51   0:00 /usr/bin/php7.1-zts /app/bxc2qlykqhbqe_stg/bin/magento cron:run --group=consumers --bootstrap=standaloneProcessStarted=1
   bxc2qly+ 25884 50.5  0.6 475472 111372 ?       R    20:51   0:01 /usr/bin/php7.1-zts /app/bxc2qlykqhbqe_stg/bin/magento cron:run --group=ddg_automation --bootstrap=standaloneProcessStarted=1
   bxc2qly+ 25890 32.5  0.6 475368 110672 ?       R    20:51   0:00 /usr/bin/php7.1-zts /app/bxc2qlykqhbqe/bin/magento cron:run --group=staging --bootstrap=standaloneProcessStarted=1
   bxc2qly+ 25892 34.5  0.6 475472 110724 ?       R    20:51   0:00 /usr/bin/php7.1-zts /app/bxc2qlykqhbqe/bin/magento cron:run --group=catalog_event --bootstrap=standaloneProcessStarted=1
   bxc2qly+ 25894 31.5  0.6 475368 110136 ?       R    20:51   0:00 /usr/bin/php7.1-zts /app/bxc2qlykqhbqe/bin/magento cron:run --group=consumers --bootstrap=standaloneProcessStarted=1
   bxc2qly+ 25896 29.0  0.6 475320 109876 ?       R    20:51   0:00 /usr/bin/php7.1-zts /app/bxc2qlykqhbqe/bin/magento cron:run --group=ddg_automation --bootstrap=standaloneProcessStarted=1
   ```

1. Se você observar uma longa [!DNL cron] tarefas que podem ser o processo de implantação de bloco, é possível encerrar o processo usando o `kill` comando. Você pode identificar o **ID do processo** (encontrou o `PID` coluna) e depois coloque isso `PID` no comando para eliminar o processo.
A variável **eliminar processo** é:

   ```kill -9 <PID>```

1. Em seguida, você pode reimplantar, se estava tentando reimplantar.
