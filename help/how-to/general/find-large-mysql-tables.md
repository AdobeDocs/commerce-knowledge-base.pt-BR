---
title: Localizar tabelas MySQL grandes
description: 'Para identificar as tabelas grandes, conecte-se ao banco de dados conforme descrito no artigo [Connect to the database](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/service/mysql#connect-to-the-database) e execute o seguinte comando, em que "project_id" é a ID do seu projeto na nuvem:'
exl-id: dc5019bc-ab6c-4568-986f-0a294a0f3ac3
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '111'
ht-degree: 0%

---

# Localizar tabelas MySQL grandes

Para identificar as tabelas grandes, conecte-se ao banco de dados conforme descrito no artigo [Conectar-se ao banco de dados](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/service/mysql#connect-to-the-database) e execute o seguinte comando, em que `project_id` é a ID do projeto na Nuvem:

```sql
SELECT TABLE_NAME AS `Table`,
  ROUND((DATA_LENGTH + INDEX_LENGTH) / 1024 / 1024) AS `Size (MB)`
FROM information_schema.TABLES
WHERE TABLE_SCHEMA = "<project_id>"
ORDER BY (DATA_LENGTH + INDEX_LENGTH) DESC;
```

Isso exibiria a lista completa de tabelas e seu tamanho. Você pode percorrer a lista e identificar quais tabelas exigem atenção devido ao tamanho grande.

## Leitura relacionada

[Práticas recomendadas para modificar tabelas de banco de dados](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) no Manual de implementação do Commerce
