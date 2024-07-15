---
title: Deadlocks no MySQL
description: Este artigo fala sobre bloqueios no MySQL para ajudar a identificá-los e resolvê-los se causarem uma inatividade do site, importação de banco de dados travada ou outros problemas do Adobe Commerce.
exl-id: 529d1c0b-77f3-4604-9878-e7ea2c9c3640
feature: Best Practices, Services
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---

# Deadlocks no MySQL

Este artigo fala sobre bloqueios no MySQL para ajudar a identificá-los e resolvê-los se causarem uma inatividade do site, importação de banco de dados travada ou outros problemas do Adobe Commerce.

## Produtos e versões afetados

* Adobe Commerce no local 2.2.x e 2.3.x
* Adobe Commerce na infraestrutura em nuvem 2.2.x e 2.3.x

## Problema

Os bloqueios no MySQL ocorrem quando duas ou mais transações são mutuamente mantidas e solicitam bloqueios. Os bloqueios que estão presentes nem sempre indicam um problema, mas geralmente são um sintoma de algum outro problema do MySQL ou do Adobe Commerce que ocorreu.

Frequentemente, o aplicativo, a implantação ou os logs do MySQL mencionarão um erro *&quot;deadlock&quot;* ou o erro *&quot;Deadlock encontrado ao tentar obter bloqueio; tente reiniciar a transação.&quot;*

## Causa

Os bloqueios podem ter várias causas, mas a mais comum é se você executar qualquer interação (site/processos/jobs cron/outros usuários/manutenção do MySQL/importações do MySQL) enquanto executa consultas DML/DDL ao mesmo tempo.

Como exemplo, é uma prática recomendada evitar uma importação de banco de dados MySQL travada, colocando primeiro o site no modo de manutenção para evitar obter solicitações SQL para o banco de dados que poderiam causar bloqueios e uma importação de banco de dados travada.

## Solução

1. Verifique se há erros de deadlock no aplicativo, na implantação ou nos logs MySQL:
   * [Locais de log do Adobe Commerce e do Magento Open Source](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/enable-logging.html)
   * [Adobe Commerce em locais de logs de infraestrutura em nuvem](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html)
1. Verifique sua lista de processos do MySQL para executar processos com o comando `mysql -e 'show full processlist';`
1. Se estiver no Adobe Commerce na infraestrutura em nuvem, verifique se o MySQL slave está ativado. Consulte este artigo: [Implantar variáveis (MYSQL\_USE\_SLAVE\_CONNECTION)](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#mysql_use_slave_connection).
1. Dependendo dos erros envolvidos, a solução pode se apresentar ou talvez você precise incluir suas informações de log úteis se precisar abrir um [Tíquete de Suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

## Leitura relacionada

* [Como Minimizar e Lidar com Deadlocks](https://dev.mysql.com/doc/refman/5.7/en/innodb-deadlocks-handling.html)
* [Otimização do Indexador - Alternância de Tabela do Indexador](https://developer.adobe.com/commerce/php/development/components/indexing/optimization/)
* [Operações em Massa - Consumir Mensagens](https://developer.adobe.com/commerce/php/development/components/message-queues/bulk-operations/)

>[!NOTE]
>
>Estamos cientes de que este artigo ainda pode conter termos de software padrão da indústria que alguns podem achar racistas, sexistas ou opressivos e que podem fazer com que o leitor se sinta ferido, traumatizado ou indesejado. O Adobe está trabalhando para remover esses termos de nosso código, documentação e experiências do usuário.
