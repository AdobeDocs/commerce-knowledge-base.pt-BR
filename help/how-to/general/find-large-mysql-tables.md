---
title: Localizar tabelas MySQL grandes
description: '"Para identificar as tabelas grandes, conecte-se ao banco de dados conforme descrito no artigo [Connect to the database](https://devdocs.magento.com/cloud/project/project-conf-files_services-mysql.html#connect-to-the-database) e execute o seguinte comando, em que "project_id" é a ID do projeto na nuvem:"'
exl-id: dc5019bc-ab6c-4568-986f-0a294a0f3ac3
source-git-commit: c1c2bd29e14f4cbfffb235801e95ec7cbb7c7a55
workflow-type: tm+mt
source-wordcount: '97'
ht-degree: 0%

---

# Localizar tabelas MySQL grandes

Para identificar as tabelas grandes, conecte-se ao banco de dados conforme descrito na seção [Conectar ao banco de dados](https://devdocs.magento.com/cloud/project/project-conf-files_services-mysql.html#connect-to-the-database) e execute o seguinte comando, onde `project_id` é a ID do projeto na nuvem:

```sql
SELECT TABLE_NAME AS `Table`,
  ROUND((DATA_LENGTH + INDEX_LENGTH) / 1024 / 1024) AS `Size (MB)`
FROM information_schema.TABLES
WHERE TABLE_SCHEMA = "<project_id>"
ORDER BY (DATA_LENGTH + INDEX_LENGTH) DESC;
```

Isso exibiria a lista completa de tabelas e seu tamanho. Você pode percorrer a lista e identificar quais tabelas exigem atenção devido ao tamanho grande.
