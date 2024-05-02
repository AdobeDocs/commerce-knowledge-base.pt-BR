---
title: Problemas de leitura de réplicas no Adobe Commerce Cloud 2.4.6 com MariaDB 10.6
description: Este artigo explica como solucionar problemas de leitura de réplicas no Adobe Commerce Cloud 2.4.6 com MariaDB 10.6.
feature: Configuration
role: Developer,Admin
exl-id: b7af1cc3-93ff-40c5-8959-076cedddb56d
source-git-commit: f12e25ac5dd607cc614dd99c90c5e104b2cee6a8
workflow-type: tm+mt
source-wordcount: '196'
ht-degree: 0%

---

# Problemas de leitura de réplicas no Adobe Commerce Cloud 2.4.6 com MariaDB 10.6

Este artigo fornece soluções para comportamento inesperado ao usar Réplicas de leitura no Adobe Commerce Cloud 2.4.6 com MariaDB 10.6+.

## Produtos e versões afetados

* MariaDB 10.6+
* Adobe Commerce na infraestrutura em nuvem 2.4.6

## Problema

As leituras não críticas estão mostrando informações incorretas.

## Causa

A variável `slave_parallel_mode` a configuração no banco de dados foi alterada por padrão para *otimistics* quando o valor deve ser *conservador*, e o `synchronous_replication` valor em Ece-Tools é padronizado como *true* quando o valor deve ser *false*.

## Solução

1. Verifique se `slave_parallel_mode` está definido como *conservador* (será necessário [criar um tíquete de suporte](/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=en#submit-ticket) se o valor não for exibido como *conservador*). Para verificar, execute o seguinte comando:

   ```
    MariaDB [main]> show variables like 'slave_parallel_mode';
    +---------------------+--------------+
    | Variable_name       | Value        |
    +---------------------+--------------+
    | slave_parallel_mode | conservative |
    +---------------------+--------------+
    1 row in set (0.001 sec)
   ```

1. Atualizar `.magento.env.yaml` configurações do banco de dados para:

   ```yaml
       DATABASE_CONFIGURATION:
        _merge: true
           slave_connection:
               default:
                   synchronous_replication: false
   ```



Para obter etapas sobre a atualização da configuração do banco de dados, consulte [DATABASE_CONFIGURATION](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#database_configuration) no tópico Implantar variáveis no Guia de infraestrutura do Commerce na nuvem.


## Leitura relacionada

* [Configurar variáveis de ambiente para implantação](/docs/commerce-cloud-service/user-guide/configure/env/configure-env-yaml.html) no Guia de infraestrutura do Commerce na nuvem.
* [Práticas recomendadas para configuração de banco de dados](/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html) no manual de implementação.
