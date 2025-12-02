---
title: Criar despejo de banco de dados no Adobe Commerce na infraestrutura em nuvem
description: Este artigo discute as possíveis (e recomendadas) maneiras de criar um despejo de banco de dados (DB) no Adobe Commerce na infraestrutura em nuvem.
exl-id: 4a2e54ac-8d65-4e51-8337-08f9748dc6c0
feature: Cloud
source-git-commit: 96b145a1f76c296907da96fd97c7a8f7778463f8
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# Criar despejo de banco de dados no Adobe Commerce na infraestrutura em nuvem

Este artigo discute as possíveis (e recomendadas) maneiras de criar um despejo de banco de dados (DB) no Adobe Commerce na infraestrutura em nuvem.

Você só precisa usar uma variante (opção) para despejar seu DB. Essas opções se aplicam a qualquer tipo de ambiente (Integração, Preparo, Produção) e a qualquer plano (arquitetura de plano Starter do Adobe Commerce na infraestrutura em nuvem e arquitetura de plano Pro do Adobe Commerce na infraestrutura em nuvem).

## Pré-requisito: SSH para o seu ambiente

Para despejar seu BD no Adobe Commerce na infraestrutura em nuvem com qualquer variante discutida neste artigo, primeiro você deve [SSH em seu ambiente](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html?lang=pt-BR).

>[!WARNING]
>
>Se você escolher a Opção 1 ou a Opção 2, execute o comando fora do horário de pico em um nó secundário do banco de dados.

## Opção 1: db-dump (**ece-tools; recommended**)

Você pode despejar seu BD usando o comando [ECE-Tools](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package.html?lang=pt-BR):

```php
vendor/bin/ece-tools db-dump
```

Essa é a opção recomendada e mais segura.

Consulte [Despejar seu banco de dados (ECE-Tools)](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/storage/database-dump.html?lang=pt-BR) no Guia de Infraestrutura do Commerce na Nuvem.

## Opção 2: mariadb-dump (ou mysqldump para versões mais antigas)

+++<b>Para versões mais recentes do MariaDB (11.x e posterior)</b>

A partir do MariaDB 11.0.1, o link simbólico `mysqldump` foi descontinuado. É recomendável usar `mariadb-dump` em seu lugar.

Para obter mais informações, consulte o [utilitário cliente de despejo mariadb](https://mariadb.com/docs/server/clients-and-utilities/backup-restore-and-import-clients/mariadb-dump).

+++

+++<b>Para versões mais antigas do MariaDB</b> 

Se você estiver em uma versão mais antiga do MariaDB, onde `mariadb-dump` não está disponível, poderá despejar seu banco de dados usando o comando nativo MySQL `mysqldump`.

>[!WARNING]
>
>Não execute este comando no cluster de banco de dados. O cluster não diferenciará se é executado no banco de dados principal ou em um secundário. Se o cluster executar esse comando em relação ao principal, o banco de dados não poderá executar gravações até que o dump seja concluído e possa afetar o desempenho e a estabilidade do site.

O comando inteiro pode parecer com o seguinte:

```sql
mysqldump -h <host> -u <username> -p <password> --single-transaction <db_name> | gzip > /tmp/<dump_name>.sql.gz
```

O backup de banco de dados criado com a execução do comando `mysqldump` e salvo em `\tmp` deve ser movido deste local. Ele não deve ocupar espaço de armazenamento em `\tmp` (o que pode resultar em problemas).

+++

Para obter suas credenciais de BD (host, nome de usuário e senha), você pode chamar a variável de ambiente `MAGENTO_CLOUD_RELATIONSHIPS`:

```
echo $MAGENTO_CLOUD_RELATIONSHIPS |base64 --d |json_pp
```

**Documentação relacionada:**

* [mysqldump - Um Programa de Backup do Banco de Dados](https://dev.mysql.com/doc/refman/8.0/en/mysqldump.html) na documentação oficial do MySQL.
* [Variáveis específicas da nuvem](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-cloud.html?lang=pt-BR) (consulte `MAGENTO_CLOUD_RELATIONSHIPS`) em nosso Guia de Infraestrutura do Commerce na Nuvem.
