---
title: Leia problemas de réplicas na Adobe Commerce Cloud 2.4.6 com MariaDB 10.6
description: Este artigo explica como solucionar problemas de leitura de réplicas na Adobe Commerce Cloud 2.4.6 com MariaDB 10.6.
feature: Configuration
role: Developer,Admin
exl-id: b7af1cc3-93ff-40c5-8959-076cedddb56d
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 0%
---
# Leia problemas de réplicas na Adobe Commerce Cloud 2.4.6 com MariaDB 10.6

Este artigo fornece soluções para comportamento inesperado ao usar Réplicas de leitura na Adobe Commerce Cloud 2.4.6 com MariaDB 10.6+.

## Produtos e versões afetados

* MariaDB 10.6+
* Adobe Commerce na infraestrutura em nuvem 2.4.6

## Problema

As leituras não críticas estão mostrando informações incorretas.

## Causa

A configuração de `slave_parallel_mode` no banco de dados foi alterada por padrão para *optimistics* quando o valor deveria ser *conservador* e o valor `synchronous_replication` em Ece-Tools usa como padrão *true* quando o valor deveria ser *false*.

## Solução

1. Verifique se o parâmetro `slave_parallel_mode` está definido como *conservador* (será necessário [criar um tíquete de suporte](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=en#submit-ticket) se o valor não estiver sendo exibido como *conservador*). Para verificar, execute o seguinte comando:

   ```
    MariaDB [main]> show variables like 'slave_parallel_mode';
    +---------------------+--------------+
    | Variable_name       | Value        |
    +---------------------+--------------+
    | slave_parallel_mode | conservative |
    +---------------------+--------------+
    1 row in set (0.001 sec)
   ```

1. Atualizar configurações do banco de dados `.magento.env.yaml` para:

   ```yaml
       DATABASE_CONFIGURATION:
        _merge: true
           slave_connection:
               default:
                   synchronous_replication: false
   ```



Para obter etapas sobre como atualizar a configuração do banco de dados, consulte [DATABASE_CONFIGURATION](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#database_configuration) no tópico Implantar variáveis no Guia de Infraestrutura do Commerce na Nuvem.


## Leitura relacionada

* [Configure as variáveis de ambiente para implantação](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/configure-env-yaml.html) no Guia de Infraestrutura do Commerce na Nuvem.
* [Práticas recomendadas para configuração de banco de dados](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html) no Manual de implementação.
