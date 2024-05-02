---
title: As tabelas MySQL são muito grandes
description: Este artigo discute por que é um problema quando qualquer tabela MySQL é maior que 1 GB e como evitar isso.
exl-id: 43f74e3b-7f2e-428c-9964-56d2ce98a34d
feature: Services
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '222'
ht-degree: 0%

---

# As tabelas MySQL são muito grandes

Este artigo discute por que é um problema quando qualquer tabela MySQL é maior que 1 GB e como evitar isso.

## Produtos e versões afetados:

* Adobe Commerce na infraestrutura em nuvem 2.x.x
* Adobe Commerce no local 2.x.x

## Problema

O tamanho das tabelas do MySQL não afeta diretamente o desempenho do site. No entanto, se uma tabela for grande, significa que há operações de inserção frequentes nessa tabela, com possíveis dados extras ou dados desatualizados. O MySQL foi projetado para bancos de dados, em que a proporção entre operações de leitura/gravação é de 80%/20%.  Para as tabelas grandes, de 1 GB ou mais, os índices MySQL, que são projetados para acelerar o desempenho em operações de leitura, podem degradar o desempenho em operações de gravação.

## Solução

Considere as seguintes opções para evitar uma redução no desempenho:

* Crie um trabalho CRON, que limpará tabelas grandes. Consulte [Localizar tabelas MySQL grandes](/help/how-to/general/find-large-mysql-tables.md) na nossa base de conhecimento de suporte para obter recomendações sobre como identificar tabelas grandes.
* Para tabelas maiores que 1 GB, use um mecanismo MySQL otimizado para gravação de logs. Por exemplo, o mecanismo Arquivo.
* Atualize a funcionalidade para evitar o armazenamento de logs no DB.

## Leitura relacionada

[Tabelas de log de alterações superdimensionadas que causam atrasos nas atualizações de entidades](/help/troubleshooting/database/changes-in-the-database-are-not-reflected-on-the-storefront.md) em nossa base de conhecimento de suporte.
