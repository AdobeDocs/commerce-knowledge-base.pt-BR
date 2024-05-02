---
title: Valor numérico do banco de dados do Adobe Commerce fora do intervalo, "INT" para "BIGINT"
description: Este artigo fornece soluções para quando não é possível salvar uma atualização de produto, como uma alteração de preço, ou excluir e duplicar um produto.
exl-id: e2a00371-9032-4e81-b60e-5456ba35be94
feature: Services
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '581'
ht-degree: 0%

---

# valor numérico do banco de dados Adobe Commerce fora do intervalo, `INT` para `BIGINT`

>[!WARNING]
>
>Antes de implementar a solução neste artigo (`INT` para `BIGINT` atualização de schema) os comerciantes devem sempre verificar se o campo que vão alterar NÃO tem nenhum relacionamento de chave estrangeira para outra tabela. Se o campo não tiver relações de chave estrangeira com outra tabela, haverá problemas porque o campo relacionado ainda está `INT`. Eles podem usar a seguinte query para verificar isso. Esta consulta lista as relações de chave estrangeira disponíveis no banco de dados para o campo de tabela especificado:
>
```mysql
>SELECT 
>     TABLE_NAME,COLUMN_NAME,CONSTRAINT_NAME,REFERENCED_TABLE_NAME,REFERENCED_COLUMN_NAME
>FROM
>   INFORMATION_SCHEMA.KEY_COLUMN_USAGE
>WHERE
>     REFERENCED_TABLE_SCHEMA = '<database_name>' AND
>     REFERENCED_TABLE_NAME = '<table_name>' AND
>     REFERENCED_COLUMN_NAME = '<table_field>';
>```

## Produtos e versões afetados

* Adobe Commerce (todos os métodos de implantação) all [versões compatíveis](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

Este artigo fornece soluções para quando não é possível salvar uma atualização de produto, como uma alteração de preço, ou excluir e duplicar um produto.
Você pode ver a mensagem de erro *Não foi possível salvar o item de estoque. Tente novamente.* Talvez não seja possível implantar o após uma atualização de produto. Você também pode ver a seguinte mensagem de erro do MySQL ao executar `php bin/magento setup:upgrade` (no Adobe Commerce na infraestrutura em nuvem, esse erro é exibido nos logs de implantação):

```mysql
SQLSTATE[22003]: Numeric value out of range: 167 Out of range value for column 'value_id' at row 1, query was: INSERT INTO `catalog_product_entity_decimal` (`attribute_id`,`store_id`,`row_id`,`value`) VALUES (?, ?, ?, ?) ON DUPLICATE KEY UPDATE `attribute_id` = VALUES(`attribute_id`), `store_id` = VALUES(`store_id`), `row_id` = VALUES(`row_id`), `value` = VALUES(`value`)
```

As soluções descritas no artigo são:
* Atualize o `[ AUTO_INCREMENT ]` ao próximo valor da tabela ou
* `INT` para `BIGINT` atualização de esquema

A solução usada depende do que causou o problema. Consulte as etapas abaixo para isolar a causa.

## Etapas para verificar a causa


Verifique o valor mais alto da chave primária executando o seguinte comando no terminal: `SELECT MAX(value_id) FROM catalog_product_entity_int;`

Se a variável `max(value_id)` é menor que `max int(11) [ 4294967296 ]`, e o `[ AUTO_INCREMENT ]` tem um valor maior ou igual ao `max int(11) [ 4294967296 ]`, considere [atualização do `[ AUTO_INCREMENT ]` ao próximo valor da tabela](#update-the-auto-increment-to-the-next-value-from-the-table). Caso contrário, considere [`INT` para `BIGINT` atualização de esquema](#int_to_bigint_schema_update).

## Atualize o `AUTO_INCREMENT` ao próximo valor da tabela {#update-the-auto-increment-to-the-next-value-from-the-table}

>[!WARNING]
>
>Execute um backup do banco de dados antes de alterar as tabelas. Além disso, coloque o site em [modo de manutenção](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/setup/application-modes.html#maintenance-mode). Além disso, também é recomendável executar o comando MYSQL otimize nas tabelas do banco de dados (somente nas tabelas em que foram feitas alterações) após fazer as alterações.

>[!NOTE]
>
>O site deve estar no modo de manutenção ao executar o comando otimizar em tabelas específicas. Isso recria totalmente as tabelas e liberará espaço após a exclusão de dados das tabelas.

Se o valor exibido for menor que `max int(11) [ 4294967296 ]` conforme mostrado no exemplo de saída de terminal abaixo, de uma tabela `[ AUTO_INCREMENT ]` foi alterado para um número maior ou igual ao `max [ int(11) ]` valor.

```mariadb
MariaDB [xxx]> SELECT MAX(value_id) FROM catalog_product_entity_int;
+---------------------+
| MAX(source_item_id) |
+---------------------+
|          4283174130 |
+---------------------+
```

Para verificar se isso ocorreu, execute o seguinte comando no terminal:

```
MariaDB [xxx]> show create table catalog_product_entity_int;

...
) ENGINE=InnoDB AUTO_INCREMENT=4294967297 DEFAULT CHARSET=utf8 COMMENT='Catalog Product Integer Attribute Backend Table';
```

Como você pode ver no exemplo acima, a saída da tabela `[ AUTO_INCREMENT ]` foi alterado para um número maior que a variável `max int(11) [ 4294967296 ]`. A solução é atualizar a `[ AUTO_INCREMENT]` para o próximo valor da tabela:

```
ALTER TABLE catalog_product_entity_int AUTO_INCREMENT = 4283174131;
```

## `INT` para `BIGINT` atualização de esquema {#int_to_bigint_schema_update}

No entanto, se ao executar a seguinte query `SELECT MAX(value_id) FROM catalog_product_entity_int;` o valor mostrado é maior que `max int(11) [ 4294967296 ]`  considere fazer uma `INT` para `BIGINT` atualização de esquema. O tipo de dados `BIGINT` O tem um intervalo maior de valores.

Para fazer isso:

1. Crie um módulo personalizado dentro do *app/code/* diretório.
1. No módulo personalizado, crie uma *db_schema.xml*. Entrada *db_schema.xml* você definirá o tipo de dados como `BIGINT`.
1. Adicione o conteúdo a seguir e execute `bin/magento setup:upgrade` para aplicar as alterações acima à tabela correspondente.

```
<?xml version="1.0"?>
<schema xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:Setup/Declaration/Schema/etc/schema.xsd">
    <table name="catalog_product_entity_int">
        <column xsi:type="bigint" name="value_id" unsigned="false" nullable="false" identity="true"
                comment="Value ID"/>
    </table>
</schema>
```


## Leitura relacionada

* [Diretrizes gerais do MySQL](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/prerequisites/database-server/mysql.html) no Guia de instalação do Commerce.
* [O upload do banco de dados perde a conexão com o MySQL](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/database/database-upload-loses-connection-to-mysql.html) em nossa base de conhecimento de suporte.
* [Práticas recomendadas de banco de dados para o Adobe Commerce na infraestrutura em nuvem](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/best-practices/database/database-best-practices-for-magento-commerce-cloud.html) em nossa base de conhecimento de suporte.
* [Problemas mais comuns de banco de dados no Adobe Commerce na infraestrutura em nuvem](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/best-practices/database/most-common-database-issues-in-magento-commerce-cloud.html) em nossa base de conhecimento de suporte.
