---
title: 'Nuvem do Adobe Commerce: a reindexação é finalizada com a mensagem "Killed"'
description: '* Adobe Commerce na infraestrutura em nuvem (todas as versões)'
exl-id: 36ed9c9f-8280-41db-9df3-fe842dade4b1
feature: Cloud, Paas
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 5a951749-fac9-5bc7-9a98-ebe4ff066437
    internal-label: Cloud
  - id: 00451af3-7b97-5414-9992-3a6c269e413f
    internal-label: Paas
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '235'
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
1. Se isso não tiver sido feito anteriormente, solicite uma atualização para os ambientes de Integração aprimorada - anote a restrição no número de ambientes aos quais você estaria limitado após a atualização ter sido executada. Consulte o artigo [Solicitação de aprimoramento do ambiente de integração - Pro e Starter](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-27242) em nossa base de dados de conhecimento de suporte para obter detalhes.

## Leitura relacionada:

Em nossa documentação do desenvolvedor:

* [Arquitetura Pro > Ambiente de integração](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/pro-architecture#integration-environment)
* [Arquitetura inicial > Ambiente de preparo](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/starter-architecture#cloud-arch-stage)
