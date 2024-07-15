---
title: Redirecionar para ambiente principal ao acessar o novo ambiente de integração
description: Este artigo fornece instruções de solução de problemas do Adobe Commerce sobre infraestrutura em nuvem, em que tentar acessar o ambiente de integração recém-criado leva você ao ambiente principal.
exl-id: d1d40c8d-d43c-442e-95c9-76f3cdcafb0e
feature: Cache, Integration, Variables
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 0%

---

# Redirecionar para ambiente principal ao acessar o novo ambiente de integração

Este artigo fornece instruções de solução de problemas do Adobe Commerce sobre infraestrutura em nuvem, em que tentar acessar o ambiente de integração recém-criado leva você ao ambiente principal.

Para corrigir isso, você precisa corrigir o valor base\_url no banco de dados e verificar se o valor da variável `UPDATE_URLS` está definido como `true`. Encontre mais detalhes nas seções abaixo.

Versões e edições afetadas:

* Adobe Commerce na infraestrutura em nuvem 2.X.X

## Problema

<u>Etapas a serem reproduzidas</u>:

1. Clonar a ramificação de Integração existente.
1. Clique no URL para acessar o novo ambiente.

<u>Resultado esperado</u>:

Você chega ao ambiente recém-criado.

<u>Resultado real</u>:

Você é redirecionado para o ambiente na ramificação principal.

## Solução

Para corrigir o problema, você precisa corrigir os valores `base_url` (seguros e não seguros) no banco de dados de ambiente personalizado e definir a variável `UPDATE_URL` no arquivo `.magento.env.yaml`.

### Corrigir valores base\_url no banco de dados

As alterações no banco de dados podem ser feitas manualmente ou usando a Adobe Commerce CLI, se você estiver na versão 2.2.0 e posterior.

#### Corrigir os valores no BD manualmente

1. Conectar ao banco de dados.
1. Execute os seguintes comandos:

```sql
UPDATE core_config_data SET value = %your_new_environment_unsecure_url% WHERE path="web/unsecure/base_url"
```

```sql
update core_config_data set value = %your_new_environment_secure_url% where path="web/secure/base_url"
```

#### Corrigir o banco de dados usando a CLI do Adobe Commerce (disponível para as versões 2.2.X)

1. Faça logon como ou alterne para o [proprietário do sistema de arquivos da Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/prerequisites/web-server/apache.html).
1. Execute os seguintes comandos:

```bash
php <your_magento_install_dir>/bin/magento config:set web/unsecure/base_url http://example.com
php <your_magento_install_dir>/bin/magento config:set web/secure/base_url https://example.com
```

### Definir a variável `UPDATE_URLS`

Em sua base de código local, no conjunto de arquivos `.magento.env.yaml`:

```
 stage:
    deploy:
        UPDATE_URLS: true
```

### Limpar cache de configuração

Para que as alterações sejam aplicadas, limpe o cache de configuração executando o seguinte comando:

```bash
php <your_magento_install_dir>/bin/magento cache:clean config
```

## Artigo relacionado em nossa documentação para desenvolvedores:

[Implantar variáveis](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html)
