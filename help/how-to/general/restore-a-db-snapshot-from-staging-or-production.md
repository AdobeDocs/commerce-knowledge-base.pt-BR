---
title: Restaurar um instantâneo do banco de dados de preparo ou produção
description: Este artigo mostra como restaurar um instantâneo do banco de dados de Preparo ou Produção na Adobe Commerce na infraestrutura em nuvem.
exl-id: 1026a1c9-0ca0-4823-8c07-ec4ff532606a
source-git-commit: 193b5118342f380cef925766c0f7956a6592800c
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# Restaurar um instantâneo de BD de [!DNL Staging] ou [!DNL Production]

Este artigo mostra como restaurar um banco de dados [!DNL snapshot] de [!DNL Staging] ou [!DNL Production] no Adobe Commerce na infraestrutura do Cloud Pro.


>[!NOTE]
>
>Estes métodos restaurarão o **instantâneo completo**.
>>Se você precisar restaurar o instantâneo **parcialmente**, por exemplo, restaurando apenas as tabelas de catálogo deixando as tabelas de ordem intactas, consulte seu desenvolvedor ou DBA.


## Produtos e versões afetados

* Adobe Commerce na infraestrutura em nuvem, [todas as versões com suporte](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

Escolha o mais apropriado para seu caso:

* [Método 1: Transfira o banco de dados [!DNL dump] para o computador local e importe-o](#meth2).
* [Método 2: importar o banco de dados [!DNL dump] diretamente do servidor](#meth3).

## Método 1: Transfira o banco de dados [!DNL dump] para o computador local e importe-o {#meth2}


>[!NOTE]
>
> O formato do instantâneo em **projetos do Azure** será diferente e conterá outros bancos de dados que **não podem ser importados**.\
> Antes de importar o instantâneo, você deve seguir etapas adicionais para **extrair o banco de dados apropriado** antes de prosseguir com a importação de despejo.

As etapas são:

1. Usando o [!DNL SFTP], navegue até o local onde o banco de dados [!DNL snapshot] foi colocado, normalmente no primeiro servidor/nó do [!DNL cluster] (Por exemplo: `/mnt/recovery-<recovery_id>`).
   > **Projetos baseados no Azure:**\
   > Se seu projeto for baseado no Azure (ou seja, sua URL de projeto se parece com `https://us-a1.magento.cloud/projects/<cluster_id>`), o instantâneo será colocado em:
   > * `/mnt/shared/<cluster ID>/all-databases.sql.gz`
   > * `/mnt/shared/<cluster ID_stg>/all-databases.sql.gz`

   **Etapas de extração específicas do Azure**

   **Para produção:**

   ```bash
   cd /mnt/shared/<cluster ID>/
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

   **Para Preparo:**

   ```bash
   cd /mnt/shared/<cluster ID_stg>/
   gunzip all-databases.sql.gz 
   head -n 17 all-databases.sql > <cluster ID_stg>.sql
   sed -n '/^-- Current Database: `<cluster ID_stg>`/,/^-- Current Database: `/p' all-databases.sql >> <cluster ID_stg>.sql 
   gzip <cluster ID_stg>.sql  
   zcat <cluster ID_stg>.sql.gz | \
   sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | \
   mysql -h 127.0.0.1 \
   -u $DB_USER \
   --password=$MYSQL_PWD $DB_NAME \
   --init-command="SET @OLD_CHARACTER_SET_CLIENT=@@CHARACTER_SET_CLIENT ;SET @OLD_CHARACTER_SET_RESULTS=@@CHARACTER_SET_RESULTS ;SET @OLD_COLLATION_CONNECTION=@@COLLATION_CONNECTION ;SET NAMES utf8 ;SET @OLD_TIME_ZONE=@@TIME_ZONE ;SET TIME_ZONE='+00:00' ;SET @OLD_UNIQUE_CHECKS=@@UNIQUE_CHECKS, UNIQUE_CHECKS=0 ;SET @OLD_FOREIGN_KEY_CHECKS=@@FOREIGN_KEY_CHECKS, FOREIGN_KEY_CHECKS=0 ;SET @OLD_SQL_MODE=@@SQL_MODE, SQL_MODE='NO_AUTO_VALUE_ON_ZERO' ;SET @OLD_SQL_NOTES=@@SQL_NOTES, SQL_NOTES=0;"
   ```

1. Copie o banco de dados [!DNL dump file] (Por exemplo: `<cluster ID>.sql.gz` para [!DNL Production] ou `<cluster ID_stg>.sql.gz` para [!DNL Staging]) no computador local.
1. Verifique se você configurou o [!DNL SSH tunnel] para se conectar ao banco de dados remotamente: [[!DNL SSH] e [!DNL sFTP]: [!DNL SSH tunneling]](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/secure-connections#env-start-tunn) em nossa documentação para desenvolvedores.
1. Conectar ao banco de dados.

   ```bash
   mysql -h <db-host> -P <db-port> -p -u <db-user> <db-name>
   ```

1. [!DNL Drop] o banco de dados; no prompt [!DNL MariaDB], digite:

   (Para [!DNL Production])

   ```bash
   drop database <cluster ID>;
   ```

   (Para [!DNL Staging])

   ```bash
   drop database <cluster ID_stg>;
   ```

1. Digite o seguinte comando para importar o [!DNL snapshot]:

   (Para [!DNL Production])

   ```bash
   zcat <cluster ID>.sql.gz | sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | mysql -h 127.0.0.1 -P <db-port> -p -u   <db-user> <db-name>
   ```

   (Para [!DNL Staging])

   ```bash
   zcat <cluster ID_stg>.sql.gz | sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | mysql -h 127.0.0.1 -P <db-port> -p -u   <db-user> <db-name>
   ```

## Método 2: importar o banco de dados [!DNL dump] diretamente do servidor {#meth3}

As etapas são:

1. Navegue até o local onde o banco de dados [!DNL snapshot] foi colocado, geralmente no primeiro servidor/nó de [!DNL cluster] (Por exemplo: `/mnt/recovery-<recovery_id>`).
1. Para [!DNL drop] e recriar o banco de dados de nuvem, primeiro conecte-se ao banco de dados:

   ```bash
   mysql -h 127.0.0.1 -P <db-port> -p -u <db-user> <db-name>
   ```

1. [!DNL Drop] o banco de dados; no prompt [!DNL MariaDB], digite:

   (Para [!DNL Production])

   ```bash
   drop database <cluster ID>;
   ```

   (Para [!DNL Staging])

   ```bash
   drop database <cluster ID_stg>;
   ```

1. Depois de soltar o banco de dados, recrie-o:

   ```bash
   create database [database_name];
   ```

1. Digite o seguinte comando para importar o [!DNL snapshot]:

   (Para importar o backup do banco de dados de [!DNL Production])

   ```bash
   zcat <cluster ID>.sql.gz | sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | mysql -h 127.0.0.1 -p -u <db-user> <db-name>
   ```

   (Para importar o backup do banco de dados de [!DNL Staging])

   ```bash
   zcat <cluster ID_stg>.sql.gz | sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | mysql -h 127.0.0.1 -p -u <db-user> <db-name>
   ```

   (Para importar um backup de banco de dados de qualquer outro ambiente)

   ```bash
   zcat <database-backup-name>.sql.gz | sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | mysql -h 127.0.0.1 -p -u <db-user> <db-name>
   ```

   (Para importar um backup de banco de dados de qualquer outro ambiente)

   ```bash
   zcat <database-backup-name>.sql.gz | sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | mysql -h 127.0.0.1 -p -u <db-user> <db-name>
   ```

## Leitura relacionada

Em nossa documentação do desenvolvedor:

* [Importar código: Importar o banco de dados](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/deploy/staging-production)
* [[!DNL Snapshots] e [!DNL backup] gerenciamento: [!DNL Dump] seu banco de dados](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/snapshots)
* [Backup (instantâneo) na nuvem: Perguntas frequentes](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/faq/backup-snapshot-on-cloud-faq)
