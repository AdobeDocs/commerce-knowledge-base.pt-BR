---
title: '[!DNL MySQL] tabelas são muito grandes'
description: Este artigo explica por que é um problema quando qualquer  [!DNL MySQL] tabela fica maior que 1 GB e como evitar isso.
exl-id: 43f74e3b-7f2e-428c-9964-56d2ce98a34d
feature: Services
role: Developer
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 0%

---

# [!DNL MySQL] tabelas são muito grandes

Este artigo discute por que é um problema quando qualquer tabela do [!DNL MySQL] fica maior que 1 GB e como evitar isso.

## Produtos e versões afetados:

* Adobe Commerce na infraestrutura em nuvem 2.x.x
* Adobe Commerce no local 2.x.x

## Problema

O tamanho das tabelas [!DNL MySQL] não afeta diretamente o desempenho do site. No entanto, se uma tabela for grande, significa que há operações de inserção frequentes nessa tabela, com possíveis dados extras ou dados desatualizados. [!DNL MySQL] foi projetado para bancos de dados, em que a proporção entre operações de leitura/gravação é de 80%/20%.  Para as tabelas grandes, com 1 GB ou mais, os índices [!DNL MySQL], que foram projetados para acelerar o desempenho em operações de leitura, podem prejudicar o desempenho em operações de gravação.

## Solução

Considere as seguintes opções para evitar uma redução no desempenho:

* Crie um trabalho CRON, que limpará tabelas grandes. Consulte [Localizar tabelas [!DNL MySQL] grandes](/help/how-to/general/find-large-mysql-tables.md) em nossa base de dados de conhecimento de suporte para obter recomendações sobre como identificar tabelas grandes.
* Para tabelas maiores que 1 GB, use um mecanismo [!DNL MySQL] otimizado para gravação de logs. Por exemplo, o mecanismo Arquivo.
* Atualize a funcionalidade para evitar o armazenamento de logs no DB.

## Leitura relacionada

* [Tabelas de log de alterações muito grandes que causam atrasos nas atualizações de entidades](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/database/changes-in-the-database-are-not-reflected-on-the-storefront) em nossa base de dados de conhecimento de suporte
* [Práticas recomendadas para modificar tabelas de banco de dados](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) no Manual de implementação do Commerce
