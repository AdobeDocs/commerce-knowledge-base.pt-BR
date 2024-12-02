---
title: O trabalho [!DNL Cron] está preso no status **em execução**
description: Este artigo fornece soluções para quando os trabalhos do Adobe Commerce [!DNL cron]  não terminarem de ser executados e persistirem em um status "em execução", o que impede a execução de outros trabalhos do  [!DNL cron] . Isso pode acontecer por vários motivos, como problemas de rede, falhas em aplicativos e problemas de reimplantação.
exl-id: 11e01a2b-2fcf-48c2-871c-08f29cd76250
feature: Configuration
role: Developer
source-git-commit: 08a241131453725a86eda5f267a209e6705da2e3
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---

# O trabalho [!DNL Cron] está preso no status &quot;em execução&quot;

Este artigo fornece soluções para quando os trabalhos do Adobe Commerce [!DNL cron] não terminarem de ser executados e persistirem em um status &quot;em execução&quot;, o que impede a execução de outros trabalhos do [!DNL cron]. Isso pode acontecer por vários motivos, como problemas de rede, falhas em aplicativos e problemas de reimplantação.

## Produtos e versões afetados

Adobe Commerce na infraestrutura em nuvem, todas as versões

## Sintoma {#symptom}

Os sintomas de [!DNL cron] trabalhos que devem ser redefinidos incluem:

* Uma grande quantidade de trabalhos aparece na fila `cron_schedule`
* O desempenho do site começa a diminuir
* Os trabalhos não são executados de acordo com o agendamento

## Soluções {#solutions}

### Solução para interromper todos os [!DNL cron] trabalhos de uma só vez {#solution-stop-all-crons-at-once}

>[!WARNING]
>
>A execução deste comando sem a opção `--job-code` redefine *todos* os trabalhos [!DNL cron], incluindo aqueles em execução no momento. Portanto, recomendamos usá-lo somente em casos excepcionais, como quando você verifica se todos os trabalhos [!DNL cron] devem ser redefinidos. A reimplantação executa esse comando por padrão para redefinir [!DNL cron] trabalhos, para que eles sejam recuperados adequadamente após o backup do ambiente. Evite usar esta solução quando os indexadores estiverem em execução.

Para resolver esse problema, você deve redefinir o(s) trabalho(s) [!DNL cron] usando o comando `cron:unlock`. Este comando altera o status do trabalho [!DNL cron] no banco de dados, encerrando o trabalho à força para permitir que outros trabalhos agendados continuem.

1. Abra um terminal e use suas [chaves SSH](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/secure-connections) para se conectar ao ambiente afetado.
1. Obtenha as credenciais do banco de dados MySQL:    ```shell    echo $MAGENTO_CLOUD_RELATIONSHIPS | base64 -d | json_pp    ```
1. Conectar ao banco de dados usando `mysql`:    ```shell    mysql -hdatabase.internal -uuser -ppassword main    ```
1. Selecione o banco de dados `main`:    ```shell    use main    ```
1. Localizar todos os [!DNL cron] trabalhos em execução:    ```shell    SELECT * FROM cron_schedule WHERE status = 'running';    ```
1. Copie o `job_code` de qualquer trabalho que esteja sendo executado por mais tempo do que o normal.
1. Use as IDs de agendamento da etapa anterior para desbloquear [!DNL cron] trabalhos específicos:    ```shell    ./vendor/bin/ece-tools cron:unlock --job-code=<job_code_1> [... --job-code=<job_code_x>]    ```

### Solução para parar um único [!DNL cron] {#solution-stop-a-single-cron}

1. Abra um terminal e use suas [chaves SSH](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/secure-connections) para se conectar ao ambiente afetado.
1. Verifique as tarefas de longa duração usando o seguinte comando:

   ```date; ps aux | grep '[%]CPU\|cron\|magento\|queue' | grep -v 'grep\|cron -f'```

1. Na saída, como na saída de exemplo abaixo, você verá a data atual e a lista de processos. A coluna `START` mostra a hora ou a data de início do processo:

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

1. Se você observar trabalhos [!DNL cron] de longa execução que possam bloquear o processo de implantação, é possível encerrar o processo usando o comando `kill`. Você pode identificar a **ID do Processo** (localizada a coluna `PID`) e colocar essa `PID` no comando para eliminar o processo.
O comando **eliminar processo** é:

   ```kill -9 <PID>```

1. Em seguida, você pode reimplantar, se estava tentando reimplantar.
