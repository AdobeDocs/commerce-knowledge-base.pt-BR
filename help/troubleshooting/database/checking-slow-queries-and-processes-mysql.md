---
title: Verificando consultas e processos lentos MySQL
description: Este artigo fala sobre alguns problemas comuns do MySQL (consultas lentas, processos demorando muito) que podem afetar negativamente o site de um comerciante e as soluções que eles indicam.
exl-id: cae02e4f-d8cb-4074-abac-24ead22bdc07
feature: Services
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 0%

---

# Verificando consultas e processos lentos MySQL

Este artigo fala sobre alguns problemas comuns do MySQL (consultas lentas, processos demorando muito) que podem afetar negativamente o site de um comerciante e as soluções que eles indicam.

## Verificação de &quot;consultas lentas&quot; do MySQL

### Descrição

Se você tiver uma interrupção possivelmente causada por um banco de dados sobrecarregado, essas etapas ajudarão a verificar o log de consultas lentas do seu banco de dados.

### Analisar consultas usando a linha de comando MySQL (Adobe Commerce Cloud/on-premise/Magento Open Source)

1. Faça logon na linha de comando do MySQL (Adobe Commerce no local/Magento Open Source) ou no servidor de nuvem na linha de comando (Adobe Commerce na infraestrutura de nuvem).
1. Examine o log de consulta lenta para consultas com mais de 50 segundos:

   ```bash
   grep 'Query_time: [5-9][0-9]\|Query_time: [0-9][0-9][0-9]' /var/log/mysql/mysql-slow.log -A 3
   ```

1. Vá para <https://www.unixtimestamp.com/> (ou um Conversor de Carimbo de Data/Hora Unix semelhante) e insira o carimbo de data/hora de quando a consulta lenta foi executada.
1. Se o tempo estiver correlacionado com qualquer interrupção de site que você tenha experimentado, pode ser causado por um banco de dados sobrecarregado. Verifique quais cargas estavam no banco de dados naquele momento. Exemplos dessas cargas:

* Processos Cron
* Tráfego (bots ou people)
* Scripts de importação/exportação
* Criação de despejos


### Analisar consultas usando o [!DNL Percona Toolkit] (Adobe Commerce Pro: somente arquitetura em nuvem)

Se seu projeto do Adobe Commerce for implantado na arquitetura Pro, você poderá usar o [!DNL Percona Toolkit] para analisar consultas.

1. Execute o comando `pt-query-digest --type=slowlog` nos logs de consulta lenta do MySQL.
   * Para encontrar o local dos logs de consulta lenta, consulte **[[!UICONTROL Log locations > Service Logs]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html)** em nossa documentação para desenvolvedores.
   * Consulte a documentação [[!DNL Percona Toolkit] > pt-query-digest](https://www.percona.com/doc/percona-toolkit/LATEST/pt-query-digest.html#pt-query-digest).
1. Com base nos problemas encontrados, siga as etapas para corrigir o query, para que ele seja executado mais rapidamente.

## Verificando a &quot;lista de processos&quot; do MySQL

### Descrição

Isso ajudará a identificar se o servidor MySQL está ativo e se não há consultas presas.

### Etapas

1. Faça logon na linha de comando do MySQL (Adobe Commerce no local/Magento Open Source) ou no servidor de nuvem na linha de comando (Adobe Commerce na infraestrutura de nuvem).
1. Faça logon no MySQL usando o bloco de código abaixo. Isso automatizará o processo de logon.

   ```MySQL
   `export DB_NAME=$(grep [\']db[\'] -A 20 app/etc/env.php | grep dbname | head -n1 | sed "s/.*[=][>][ ]*[']//" | sed "s/['][,]//");    export MYSQL_HOST=$(grep [\']db[\'] -A 20 app/etc/env.php | grep host | head -n1 | sed "s/.*[=][>][ ]*[']//" | sed "s/['][,]//");    export DB_USER=$(grep [\']db[\'] -A 20 app/etc/env.php | grep username | head -n1 | sed "s/.*[=][>][ ]*[']//" | sed "s/['][,]//");    export MYSQL_PWD=$(grep [\']db[\'] -A 20 app/etc/env.php | grep password | head -n1 | sed "s/.*[=][>][ ]*[']//" | sed "s/[']$//" | sed "s/['][,]//");    mysql -h $MYSQL_HOST -u $DB_USER --password=$MYSQL_PWD $DB_NAME -U -A -e 'show processlist;`
   ```

1. Se você receber um erro de volta ou se a resposta demorar mais de 30 segundos, entre em contato com o suporte para verificar o servidor MySQL.
1. Observando a saída de exemplo.

1. Este é um exemplo de saída:

   ```MySQL
   `$ mysql -h $MYSQL_HOST -u $DB_USER --password=$MYSQL_PWD $DB_NAME -U -A -e 'show processlist;'    +-----------+---------------+--------------------+---------------+---------+------+----------------+------------------------------------------------------------------------------------------------------+----------+    | Id        | User          | Host               | db            | Command | Time | State          | Info                                                                                                 | Progress |    +-----------+---------------+--------------------+---------------+---------+------+----------------+------------------------------------------------------------------------------------------------------+----------+    | 123456789 | abcdefghijklm | 192.168.7.10:12345 | abcdefghijklm | Query   |    0 | Writing to net | SELECT `magento_versionscms_hierarchy_node`.*, `page_table`.`title` AS `page_title`, `page_table`.`i |    0.000 |    | 123456788 | abcdefghijklm | 192.168.7.10:12344 | abcdefghijklm | Sleep   |    0 |                | NULL                                                                                                 |    0.000 |    | 123456777 | abcdefghijklm | 192.168.7.10:12333 | abcdefghijklm | Sleep   |    0 |                | NULL                                                                                                 |    0.000 |    | 123456666 | abcdefghijklm | 192.168.5.8:12222  | abcdefghijklm | Sleep   |    0 |                | NULL                                                                                                 |    0.000 |`
   ```

1. Verifique a coluna &quot;Tempo&quot; para qualquer tempo superior a 1800 segundos; isso indica que um processo está possivelmente demorando muito para ser concluído. Observe o status dos processos na coluna &quot;Estado&quot;.
1. Revise as consultas e possivelmente elimine-as se elas não forem executadas por esse período. É possível que as consultas de longa execução sejam esperadas.


## Leitura relacionada

* [Sintaxe MySQL Show Processlist](https://dev.mysql.com/doc/refman/8.0/en/show-processlist.html) em dev.mysql.com.
* [Sintaxe de eliminação do MySQL](https://dev.mysql.com/doc/refman/8.0/en/kill.html) em dev.mysql.com.
* [Segurança, desempenho e manuseio de dados](https://developer.adobe.com/commerce/php/best-practices/extensions/security/) na documentação do desenvolvedor.
* [Ajuda do MySQL](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/database-server/mysql) em nossa documentação para desenvolvedores.
