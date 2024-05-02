---
title: '"Nuvem do Adobe Commerce: a reindexação é encerrada com a mensagem "Eliminado""'
description: '* Adobe Commerce na infraestrutura em nuvem (todas as versões)'
exl-id: 36ed9c9f-8280-41db-9df3-fe842dade4b1
feature: Cloud, Paas
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '198'
ht-degree: 0%

---

# Nuvem do Adobe Commerce: a reindexação é encerrada com `Killed` mensagem

## Produtos e versões afetados

* Adobe Commerce na infraestrutura em nuvem (todas as versões)

## Problema

Você está tentando executar uma reindexação na ramificação de integração (ou no ambiente de preparo do projeto de arquitetura inicial) e o processo está sendo encerrado com o `Killed` mensagem.

## Causa

Isto geralmente acontece porque os processos PHP estão ficando sem memória.
O motivo mais comum para isso é um grande número de produtos, lojas e/ou grupos de clientes na instância.

## Solução

1. Reduzir o número de produtos (bem como de grupos de clientes e lojas, se aplicável).
1. Limitar o uso a um ou dois usuários simultâneos.
1. Desative os trabalhos cron e execute manualmente conforme necessário.
1. Se isso não tiver sido feito anteriormente, solicite uma atualização para os ambientes de Integração aprimorada - anote a restrição no número de ambientes aos quais você estaria limitado após a atualização ter sido executada. Consulte a [Solicitação de aprimoramento do ambiente de integração - Pro e Starter](/help/announcements/adobe-commerce-announcements/integration-environment-enhancement-request-pro-and-starter.md) para obter mais detalhes, consulte este artigo em nossa base de conhecimento de suporte.

## Leitura relacionada:

Em nossa documentação do desenvolvedor:

* [Arquitetura Pro > Ambiente de integração](https://devdocs.magento.com/cloud/architecture/pro-architecture.html#cloud-arch-int)
* [Arquitetura inicial > Ambiente de preparo](https://devdocs.magento.com/cloud/architecture/starter-architecture.html#cloud-arch-stage)
