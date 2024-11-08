---
title: O upload do banco de dados perde a conexão com o MySQL
description: Este artigo fornece uma solução para quando o upload do banco de dados perde a conexão com o MySQL.
exl-id: 6051cea1-8292-4a81-8908-eb516cb4a32b
feature: Services
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '229'
ht-degree: 0%

---

# O upload do banco de dados perde a conexão com o MySQL

Este artigo fornece uma solução para quando o upload do banco de dados perde a conexão com o MySQL.

## Produtos e versões afetados

Adobe Commerce na infraestrutura em nuvem 2.2.x., 2.3.x

## Problema

O banco de dados não é carregado nas ramificações principal/de integração na arquitetura de plano do Adobe Commerce na infraestrutura em nuvem Pro ou em qualquer ramificação na arquitetura de plano do Adobe Commerce na infraestrutura em nuvem Starter, com o sintoma sendo a incapacidade de se conectar. Esse erro é exibido na CLI.

```
web@ddc35c264bd89a72042f1f3e5a:~$ mysql -h database.internal -u user -p main
Enter password:
ERROR 2013 (HY000): Lost connection to MySQL server at 'reading initial communication packet', system error: 0 "Internal error/check (Not system error)"
```

## Causa

Isso geralmente ocorre devido à falta de espaço em disco para importar o banco de dados.

## Solução

Verifique se há falta de espaço em disco. Para fazer isso, execute o comando `netcat` na CLI em relação à porta de banco de dados 3306; haverá uma mensagem de disco cheio se estiver cheio:

```
web@ddc35c264bd89a72042f1f3e5a:~$ nc database.internal 3306
Database out of space
```

Será necessário alocar mais espaço para o banco de dados no `services.yaml` e implantar se houver espaço não utilizado. Para obter as etapas, consulte [Espaço em Disco do Serviço](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space#service-disk-space).

Observação: no plano Pro architecture, você pode verificar o espaço alocado em sua partição executando o seguinte comando: `df -h`

Espere uma saída semelhante à seguinte. Neste exemplo, 10 GB dos 25 GB alocados são usados, com 15 GB de espaço MySQL não sendo usados.

```
f240jestone3wt@i-087r2a25fdac80726:~$ df -h|grep 'File\|xvd'
Filesystem                                         Size  Used Avail Use% Mounted on
/dev/xvda1                                          59G   15G   42G  26% /
/dev/xvdj                                           25G   10G   15G  41% /data/mysql
/dev/xvdi                                           25G   22G  2.6G  90% /data/exports
```

## Leitura relacionada

[Gerenciar espaço em disco](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space) na documentação do desenvolvedor
