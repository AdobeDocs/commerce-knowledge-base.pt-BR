---
title: Solução de problemas de montagem /tmp completa para o Adobe Commerce
description: Este artigo fornece uma solução para quando a montagem `/tmp` estiver cheia, o site puder estar inativo e você não conseguir aplicar SSH a um nó.
exl-id: e72d0f99-0060-474b-bb1c-2851896e1e43
feature: Storage
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '625'
ht-degree: 0%

---

# Solução de problemas de montagem /tmp completa para o Adobe Commerce

Este artigo fornece uma solução para quando a montagem do `/tmp` estiver cheia, o site pode estar inativo e você não pode executar SSH em um nó.

## Produtos e versões afetados

* Adobe Commerce 2.3.0 - 2.3.6-p1, 2.4.0 - 2.4.2

## Problema

A montagem `/tmp` pode resultar em vários sintomas possíveis, incluindo os seguintes erros:

* *SQLSTATE[HY000]: Erro geral: 3 Erro ao gravar arquivo*
* *Código de erro: 28*
* *Não há mais espaço no dispositivo (28)*
* *erro session_start(): falha: sem espaço no dispositivo*
* *ERRO 1 (HY000): não é possível criar/gravar no arquivo &#39;/tmp/*
* *Erro de SQL: 3, SQLState: HY000*
* *Erro geral: 1021 Disco cheio (/tmp)*
* *Não é possível acessar o nó via SSH:*
  *bash: não é possível criar arquivo temporário para here-document: sem espaço no dispositivo*
* *errno: 28 &quot;Não há espaço disponível no dispositivo&quot;*
* *mysqld: disco com gravação completa &#39;/tmp&#39;*
* *[ERRO] mysqld: disco cheio (/tmp)*
* *SQLSTATE[HY000]: erro geral: 1 Não é possível criar/gravar no arquivo &#39;/tmp/&#39;*
* *SQLSTATE[HY000]: erro geral: 23 recursos insuficientes ao abrir o arquivo &#39;/tmp/&#39;*
* *Errcode: 24 &quot;Muitos arquivos abertos&quot;*
* *Erro recebido: 23: recursos insuficientes ao abrir o arquivo*


<u>Etapas a serem reproduzidas:</u>

Para verificar se a montagem `/tmp` está cheia, no switch CLI para `/tmp` e execute o seguinte comando:

```bash
 df -h
```

<u>Resultado esperado</u>:

Menos de 80%.

<u>Resultado real</u>:

Em torno de 100%.

## Causa

A montagem `/tmp` tem muitos arquivos, o que pode ser causado por:

* Consultas SQL incorretas gerando tabelas temporárias grandes e/ou muitas.
* Serviços gravando no diretório `/tmp`.
* Backups/despejos de banco de dados deixados no diretório `/tmp`.

## Solução

Há coisas que você pode fazer para liberar espaço uma vez, e há práticas recomendadas que impediriam `\tmp` de ficar cheio.

### Verificar e liberar inodes

Verifique se há inodes disponíveis suficientes. Para fazer isso, execute o seguinte comando:

```bash
df -i
```

A saída seria semelhante ao seguinte:

```bash
Filesystem Inodes   Used   Free Use% Mounted on
/dev/nvme2n1 655360    1695  653665    1% /data/mysql
```

Verifique se % de uso é &lt;70%. Os nós estão correlacionados com os arquivos. Se você remover arquivos da partição, liberará inodes.

### Verificar e liberar espaço de armazenamento

Há vários serviços que podem estar salvando arquivos em `/tmp`.

#### Verificar e liberar espaço no MySQL

Siga as instruções em [O espaço em disco do MySQL é insuficiente no Adobe Commerce na infraestrutura de nuvem > Verificar e liberar espaço de armazenamento](/help/troubleshooting/database/mysql-disk-space-is-low-on-magento-commerce-cloud.md#check_and_free) em nossa base de dados de suporte.

#### Verificar Elasticsearch heapdumps

>[!WARNING]
>
>Os despejos de pilha contêm informações de registro que podem ser valiosas para investigar problemas. Considere armazená-los em um local separado por, pelo menos, 10 dias.

Remover despejos de pilha (`*.hprof`) usando o shell do sistema:

```bash
find /tmp/*.hprof -type f -delete
```

Se você não tiver permissões para excluir arquivos criados por outro usuário (neste caso, Elasticsearch), mas perceber que os arquivos são grandes, [crie um tíquete de suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) para lidar com eles.

#### Verificar despejos/backups do banco de dados

>[!WARNING]
>
>Geralmente, os backups do banco de dados são criados para uma finalidade. Se não tiver certeza se o arquivo ainda é necessário, considere movê-lo para um local separado em vez de excluí-lo.

Verifique `/tmp` para arquivos `.sql` ou `.sql.gz` e limpe-os. Eles podem ter sido criados por ece-tools durante o backup ou ao criar manualmente despejos de banco de dados usando a ferramenta `mysqldump`.

### Práticas recomendadas

Para evitar problemas com o `/tmp` cheio, siga estas recomendações:

* Não use MySQL para pesquisa. O Elasticsearch para pesquisa geralmente elimina a necessidade da maioria das criações pesadas de tabelas temporárias. Consulte [Configurar o Adobe Commerce para usar o Elasticsearch](https://devdocs.magento.com/guides/v2.2/config-guide/elasticsearch/configure-magento.html) na documentação do desenvolvedor.
* Evite executar a consulta `SELECT` em colunas sem índices, pois isso consome uma grande quantidade de espaço temporário em disco. Você também pode adicionar os índices.
* Crie um cron para limpar `/tmp` executando o seguinte comando na CLI:

  ```bash
  sudo find /tmp -type f -atime +10 -delete
  ```

## Leitura relacionada

[O espaço em disco do MySQL é insuficiente na infraestrutura de nuvem do Adobe Commerce](/help/troubleshooting/database/mysql-disk-space-is-low-on-magento-commerce-cloud.md) em nossa base de dados de conhecimento de suporte.
