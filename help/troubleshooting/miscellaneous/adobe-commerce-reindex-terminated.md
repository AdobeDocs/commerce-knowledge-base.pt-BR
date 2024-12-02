---
title: 'Nuvem do Adobe Commerce: a reindexação é finalizada com a mensagem "Killed"'
description: '* Adobe Commerce na infraestrutura em nuvem (todas as versões)'
exl-id: 36ed9c9f-8280-41db-9df3-fe842dade4b1
feature: Cloud, Paas
role: Developer
source-git-commit: 8b6bf1cdada7edb0cdb0bb3e90ed15ee8cebf77e
workflow-type: tm+mt
source-wordcount: '198'
ht-degree: 0%

---

# Nuvem do Adobe Commerce: a reindexação foi finalizada com a mensagem `Killed`

## Produtos e versões afetados

* Adobe Commerce na infraestrutura em nuvem (todas as versões)

## Problema

Você está tentando executar uma reindexação na ramificação de Integração (ou na Preparação do projeto de arquitetura de Início), e o processo está sendo encerrado com a mensagem `Killed`.

## Causa

Isto geralmente acontece porque os processos PHP estão ficando sem memória.
O motivo mais comum para isso é um grande número de produtos, lojas e/ou grupos de clientes na instância.

## Solução

1. Reduzir o número de produtos (bem como de grupos de clientes e lojas, se aplicável).
1. Limitar o uso a um ou dois usuários simultâneos.
1. Desative os trabalhos cron e execute manualmente conforme necessário.
1. Se isso não tiver sido feito anteriormente, solicite uma atualização para os ambientes de Integração aprimorada - anote a restrição no número de ambientes aos quais você estaria limitado após a atualização ter sido executada. Consulte o artigo [Solicitação de aprimoramento do ambiente de integração - Pro e Starter](/help/announcements/adobe-commerce-announcements/integration-environment-enhancement-request-pro-and-starter.md) em nossa base de dados de conhecimento de suporte para obter detalhes.

## Leitura relacionada:

Em nossa documentação do desenvolvedor:

* [Arquitetura Pro > Ambiente de integração](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/pro-architecture#integration-environment)
* [Arquitetura inicial > Ambiente de preparo](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/starter-architecture#cloud-arch-stage)
