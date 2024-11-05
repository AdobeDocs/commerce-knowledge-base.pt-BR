---
title: Erro de processamento do Sistema Magento Order Management (OMS) para Adobe Commerce
description: Este artigo fornece uma solução para o problema quando você recebe um erro "getMode()" na CLI que executa "bin/magento oms:messages:process" no Sistema de Magento Order Management (OMS) do Adobe Commerce.
exl-id: 83089465-f810-4a3b-bdb6-4720b44f0b49
feature: System
role: Developer
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '217'
ht-degree: 0%

---

# Erro de processamento do Sistema Magento Order Management (OMS) para Adobe Commerce

Este artigo fornece uma solução para o problema que ocorre quando você recebe um erro `getMode()` na CLI que executa o `bin/magento oms:messages:process` no OMS (Magento Order Management System) para Adobe Commerce.

## Produtos e versões afetados

Esse erro ocorre ao usar o Conector do MCOM versões 3.1.1 e 3.2.0. É resolvido no Conector MCOM 3.3.0. Não é específico de uma versão MDC ou MOM.

## Problema

Ao executar o seguinte comando na CLI:

`bin/magento oms:messages:process`

Uma mensagem de erro semelhante à seguinte é exibida na CLI:

```
<project-id>@<project-id>:~$ php bin/magento oms:messages:process

Processing messages...

PHP Fatal error:Uncaught Error: Call to a member function getMode()
on null in /app/<project-id>/vendor/magento/module-inventory-message-bus/Handler/OnAggregateStockUpdatedSubscriber.php:64

Stack trace:

  #0 [internal function]: Magento\InventoryMessageBus\Handler\OnAggregateStockUpdatedSubscriber->onUpdated(Object(Magento\InventoryMessageBus\Model\Event\OnAggregateStockUpdated))

  #1 /app/<project-id>/vendor/magento/module-service-bus/Message/SingleMessageProcessor.php(81):
  call_user_func(Array, Object(Magento\InventoryMessageBus\Model\Event\OnAggregateStockUpdated))

  #2 [internal function]: Magento\ServiceBus\Message\SingleMessageProcessor->Magento\ServiceBus\Message\\{closure}(Array)

  #3 /app/<project-id>/vendor/magento/module-service-bus/Message/SingleMessageProcessor.php(86):
  array_map(Object(Closure), Array)

  #4 /app/<project-id>/vendor/magento/module-service-bus/Message/Processor.php(110):
  Magento\ServiceBus\Message\SingleMessageProcessor->process(Object(Magento\CommonMessageBus\Message\Message))

  #5 /app/t in /app/<project-id>/vendor/magento/module-inventory-message-bus/Handler/OnAggregateStockUpdatedSubscriber.php
  on line 64
```

## Causa

Â
Isso ocorre quando o Conector tenta processar `magento.inventory.source_management` mensagens. O Conector tenta processar essas mensagens como se elas fossem uma mensagem `magento.inventory.source_stock_management.update` que requer um valor de modo. O erro ocorre porque não há modo nas mensagens `magento.inventory.source_mangement`.

## Solução

Para resolver o problema, execute a seguinte instrução [!DNL SQL] na CLI, que exclui todos os registros da tabela `mcom_api_messages`:

`delete from mcom_api_messages;`

## Leitura relacionada

* Documentação do OMS [Tutorial de Instalação do Conector OMS](https://omsdocs.magento.com/en/integration/connector/setup-tutorial/)
* [Práticas recomendadas para modificar tabelas de banco de dados](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) no Manual de implementação do Commerce
