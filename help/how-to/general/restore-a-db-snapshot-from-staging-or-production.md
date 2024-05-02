---
title: Restaurar um instantâneo do banco de dados de preparo ou produção
description: Este artigo mostra como restaurar um instantâneo do banco de dados de Preparo ou Produção na Adobe Commerce na infraestrutura em nuvem.
exl-id: 1026a1c9-0ca0-4823-8c07-ec4ff532606a
source-git-commit: b9e72ff8d541ad01788e5198e03abcb46a1bd11f
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 0%

---

# Restaurar um instantâneo do BD a partir de [!DNL Staging] ou [!DNL Production]

Este artigo mostra como restaurar um BD [!DNL snapshot] de [!DNL Staging] ou [!DNL Production] na infraestrutura do Adobe Commerce na Cloud Pro.

## Produtos e versões afetados

* Adobe Commerce na infraestrutura em nuvem, [todas as versões compatíveis](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

Escolha o mais apropriado para seu caso:

* [Método 1: transferir o banco de dados [!DNL dump] para o computador local e importe-o](#meth2).
* [Método 2: importar o banco de dados [!DNL dump] diretamente do servidor](#meth3).

## Método 1: transferir o banco de dados [!DNL dump] para o computador local e importe-o {#meth2}

As etapas são:

1. Usar [!DNL sFTP], navegue até o local onde o banco de dados [!DNL snapshot] foi colocado, geralmente no primeiro servidor/nó de sua [!DNL cluster] (Por exemplo: `/mnt/recovery-<recovery_id>`). OBSERVAÇÃO: se seu projeto for baseado no Azure, ou seja, o URL do projeto será semelhante ao https://us-a1.magento.cloud/projects/&lt;cluster_id>, o instantâneo será colocado em `/mnt/shared/<cluster ID>/all-databases.sql.gz` ou `/mnt/shared/<cluster ID_stg>/all-databases.sql.gz` em vez disso.

   OBSERVAÇÃO: o formato do instantâneo nos projetos do Azure será diferente e conterá outros bancos de dados que não podem ser importados. Antes de importar o snapshot, você terá que executar etapas adicionais para extrair o banco de dados apropriado antes de importar o dump.

   Para produção:

   ```sql
   cd /mnt/shared/<cluster ID/
   gunzip all-databases.sql.gz 
   head -n 17 all-databases.sql > <cluster ID>.sql 
   sed -n '/^-- Current Database: `<cluster ID>`/,/^-- Current Database: `/p' all-databases.sql >> <cluster ID>.sql gzip <cluster ID>.sql
   zcat <cluster ID>.sql.gz | \
   sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | \
   mysql -h 127.0.0.1 \
   -u $DB_USER \
   --password=$MYSQL_PWD $DB_NAME \
   --init-command="SET @OLD_CHARACTER_SET_CLIENT=@@CHARACTER_SET_CLIENT ;SET @OLD_CHARACTER_SET_RESULTS=@@CHARACTER_SET_RESULTS ;SET @OLD_COLLATION_CONNECTION=@@COLLATION_CONNECTION ;SET NAMES utf8 ;SET @OLD_TIME_ZONE=@@TIME_ZONE ;SET TIME_ZONE='+00:00' ;SET @OLD_UNIQUE_CHECKS=@@UNIQUE_CHECKS, UNIQUE_CHECKS=0 ;SET @OLD_FOREIGN_KEY_CHECKS=@@FOREIGN_KEY_CHECKS, FOREIGN_KEY_CHECKS=0 ;SET @OLD_SQL_MODE=@@SQL_MODE, SQL_MODE='NO_AUTO_VALUE_ON_ZERO' ;SET @OLD_SQL_NOTES=@@SQL_NOTES, SQL_NOTES=0;"
   ```

   Para Preparo:

   ```sql
   cd /mnt/shared/<cluster ID/ | cd /mnt/shared/<cluster ID_stg>
   gunzip all-databases.sql.gz 
   head -n 17 all-databases.sql > <cluster ID_stg>.sql
   sed -n '/^-- Current Database: `wyf2o4zlrljjs`/,/^-- Current Database: `/p' all-databases.sql >> <cluster ID_stg>.sql 
   gzip <cluster ID_stg>.sql  
   zcat <cluster ID_stg>.sql.gz | \
   sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | \
   mysql -h 127.0.0.1 \
   -u $DB_USER \
   --password=$MYSQL_PWD $DB_NAME \
   --init-command="SET @OLD_CHARACTER_SET_CLIENT=@@CHARACTER_SET_CLIENT ;SET @OLD_CHARACTER_SET_RESULTS=@@CHARACTER_SET_RESULTS ;SET @OLD_COLLATION_CONNECTION=@@COLLATION_CONNECTION ;SET NAMES utf8 ;SET @OLD_TIME_ZONE=@@TIME_ZONE ;SET TIME_ZONE='+00:00' ;SET @OLD_UNIQUE_CHECKS=@@UNIQUE_CHECKS, UNIQUE_CHECKS=0 ;SET @OLD_FOREIGN_KEY_CHECKS=@@FOREIGN_KEY_CHECKS, FOREIGN_KEY_CHECKS=0 ;SET @OLD_SQL_MODE=@@SQL_MODE, SQL_MODE='NO_AUTO_VALUE_ON_ZERO' ;SET @OLD_SQL_NOTES=@@SQL_NOTES, SQL_NOTES=0;"
   ```

1. Copiar o banco de dados [!DNL dump file] (Por exemplo: `<cluster ID>.sql.gz` para [!DNL Production] ou `<cluster ID_stg>.sql.gz` para [!DNL Staging]) ao computador local.
1. Verifique se você configurou o [!DNL SSH tunnel] para conectar-se ao banco de dados remotamente: [[!DNL SSH] e [!DNL sFTP]: [!DNL SSH tunneling]](https://devdocs.magento.com/cloud/env/environments-ssh.html#env-start-tunn) na documentação do desenvolvedor.
1. Conectar ao banco de dados.

   ```sql
   mysql -h <db-host> -P <db-port> -p -u <db-user> <db-name>
   ```

1. [!DNL Drop] o banco de dados; no [!DNL MariaDB] digite:

   (Para [!DNL Production])

   ```sql
   drop database <cluster ID>;
   ```

   (Para [!DNL Staging])

   ```sql
   drop database <cluster ID_stg>;
   ```

1. Digite o seguinte comando para importar o [!DNL snapshot]:

   (Para [!DNL Production])

   ```sql
   zcat <cluster ID>.sql.gz | sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | mysql -h 127.0.0.1 -P <db-port> -p -u   <db-user> <db-name>
   ```

   (Para [!DNL Staging])

   ```sql
   zcat <cluster ID_stg>.sql.gz | sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | mysql -h 127.0.0.1 -P <db-port> -p -u   <db-user> <db-name>
   ```

## Método 2: importar o banco de dados [!DNL dump] diretamente do servidor {#meth3}

As etapas são:

1. Navegue até o local onde o banco de dados [!DNL snapshot] foi colocado, geralmente no primeiro servidor/nó de sua [!DNL cluster] (Por exemplo: `/mnt/recovery-<recovery_id>`).
1. Para [!DNL drop] e recriar o banco de dados em nuvem, primeiro conecte-se ao banco de dados:

   ```sql
   mysql -h 127.0.0.1 -P <db-port> -p -u <db-user> <db-name>
   ```

1. [!DNL Drop] o banco de dados; no [!DNL MariaDB] digite:

   (Para [!DNL Production])

   ```sql
   drop database <cluster ID>;
   ```

   (Para [!DNL Staging])

   ```sql
   drop database <cluster ID_stg>;
   ```

1. Digite o seguinte comando para importar o [!DNL snapshot]:

   (Para [!DNL Production])

   ```sql
   zcat <cluster ID>.sql.gz | sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | mysql -h 127.0.0.1 -p -u <db-user> <db-name>
   ```

   (Para [!DNL Staging])

   ```sql
   zcat <cluster ID_stg>.sql.gz | sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | mysql -h 127.0.0.1 -p -u <db-user> <db-name>
   ```

## Leitura relacionada

Em nossa documentação do desenvolvedor:

* [Importar código: Importar o banco de dados](https://devdocs.magento.com/cloud/setup/first-time-setup-import-import.html#cloud-import-db)
* [[!DNL Snapshots] e [!DNL backup] gerenciamento: [!DNL Dump] seu banco de dados](https://devdocs.magento.com/cloud/project/project-webint-snap.html#db-dump)
