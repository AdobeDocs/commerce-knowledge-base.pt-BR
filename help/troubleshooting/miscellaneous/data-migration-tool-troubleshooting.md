---
title: Solução de problemas da Ferramenta de migração de dados
description: Este artigo fornece soluções para erros que podem ocorrer ao executar a Ferramenta de migração de dados.
exl-id: 9beb31ae-ed3c-42e1-b0bf-33fb1c91e0ea
feature: Data Import/Export
role: Developer
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '741'
ht-degree: 0%

---

# Solução de problemas da Ferramenta de migração de dados

Este artigo fornece soluções para erros que podem ocorrer ao executar a Ferramenta de migração de dados.

## Documentos/campos do Source não mapeados {#source-documents-fields-not-mapped}

### Mensagens de erro

* ```bash    Source documents are not mapped: <EXTENSION_TABLE>    ```
* ```bash    Source fields are not mapped. Document: <EXTENSION_TABLE>. Fields: <EXTENSION_FIELD>    ```

Em casos raros, a mensagem pode mencionar

```bash
Destination documents
```

ou

```bash
Destination fields
```

em vez dos de origem.

### Causa

Algumas entidades do Adobe Commerce versão 1 (na maioria dos casos, provenientes de extensões) não existem no banco de dados do Adobe Commerce versão 2.

Esta mensagem é exibida porque a Ferramenta de Migração de Dados executa testes internos para verificar se as tabelas e os campos estão consistentes entre os bancos de dados de *origem* (Adobe Commerce 1) e *destino* (Adobe Commerce 2).

### Possíveis soluções

* Instale as extensões correspondentes do Adobe Commerce 2 de [Commerce Marketplace](https://marketplace.magento.com/).     Se os dados conflitantes forem originários de uma extensão que adiciona elementos de estrutura de banco de dados próprios, a versão Adobe Commerce 2 da mesma extensão poderá adicionar esses elementos ao banco de dados de destino (Adobe Commerce 2), corrigindo o problema.
* Use o argumento `-a` ao executar a ferramenta para resolver erros automaticamente e impedir que a migração seja interrompida.
* Configure a Ferramenta para ignorar os dados problemáticos.

Para ignorar entidades de banco de dados, adicione a marca `<ignore>` a uma entidade no arquivo `map.xml`, desta forma:

```xml
...
    <source>
        <document_rules>
            ...
            <!-- Ignore `sales_flat_invoice_grid` table -->
            <ignore>
                <document>sales_flat_invoice_grid</document>
            </ignore>
            <!-- Ignore `address_id` field of `sales_flat_order_address` table -->
            <ignore>
                <field>sales_flat_order_address.address_id</field>
            </ignore>
            ...
        </document_rules>
    </source>
    ...
```

>[!WARNING]
>
>Antes de ignorar entidades pelo arquivo de mapa ou usar a opção `-a`, verifique se você não precisa dos dados afetados no armazenamento do Adobe Commerce 2.

## A classe não está mapeada no registro {#class-does-not-exist-but-mentioned}

### Mensagem de erro

```bash
Class <extension/class_name> is not mapped in record <attribute_id=196>
```

### Causa

Não foi possível encontrar uma classe da base de código do Adobe Commerce 1 na base de código do Adobe Commerce 2 durante a [etapa de migração do EAV](https://devdocs.magento.com/guides/v2.3/migration/migration-tool-internal-spec.html#eav) da documentação do desenvolvedor. Na maioria dos casos, a classe ausente pertence a uma [extensão](https://glossary.magento.com/extension).

### Possíveis soluções

* Instale a extensão correspondente do Adobe Commerce 2.
* Ignore o atributo que causa o problema.    Para isso, adicione o atributo ao grupo `ignore` no arquivo `eav-attribute-groups.xml.dist`.
* Adicionar mapeamento de classe usando o arquivo `class-map.xml.dist`.

## Falha na restrição de chave estrangeira

### Texto da mensagem de erro

```bash
Foreign key <KEY_NAME> constraint fails on source database. Orphan records id: <id_1>, <id_2> from <child_table>.<field_id> has no referenced records in <parent_table>
```

### Causa

Faltam registros de banco de dados no `parent_table` para o qual `field_id` de `child_table` está apontando.

### Possível solução

Exclua os registros de `child_table` , se não precisar deles.

Para manter os registros, desabilite o `Data Integrity Step` modificando o `config.xml` da Ferramenta de Migração de Dados.

## Duplicatas em regravações de URL

```xml
There are duplicates in URL rewrites:
Request path: towel.html Store ID: 2 Target path: catalog/product/view/id/10
Request path: towel.html Store ID: 2 Target path: catalog/product/view/id/12
```

### Causa

O `Target path` em uma regravação de URL deve ser especificado por um par exclusivo de `Request path` + `Store ID`. Este erro relata duas entradas que usam o mesmo par `Request path` + `Store ID` com dois valores `Target path` diferentes.

### Possível solução

Habilite a opção `auto_resolve_urlrewrite_duplicates` no arquivo `config.xml`.

Esta configuração adiciona uma cadeia de caracteres de hash aos registros conflitantes de [URL](https://glossary.magento.com/url) regravações e mostra o resultado da resolução na interface de linha de comando.

## Incompatibilidade de entidades {#mismatch-of-entities}

### Mensagem de erro

```bash
Mismatch of entities in the document: <DOCUMENT> Source: <COUNT_ITEMS_IN_SOURCE_TABLE> Destination: <COUNT_ITEMS_IN_DESTINATION_TABLE>
```

### Causa

O erro ocorre durante a etapa de verificação de volume. Isso significa que a contagem de registros do banco de dados do Adobe Commerce 2 do documento não é a mesma que no Adobe Commerce 1.

Os registros ausentes ocorrem quando um cliente faz um pedido durante a migração.

### Possível solução

Execute a Ferramenta de Migração de Dados no modo `Delta` para transferir alterações incrementais.

## O Deltalog não está instalado {#deltalog-is-not-installed}

### Mensagem de erro

```bash
Deltalog for <TABLE_NAME> is not installed
```

### Causa

Este erro ocorre durante a [migração incremental](https://devdocs.magento.com/guides/v2.3/migration/migration-migrate-delta.html) (na documentação do desenvolvedor) de alterações nos dados. Isso significa que as tabelas de exclusão (com o prefixo `m2_cl_*`) não foram encontradas no banco de dados do Adobe Commerce 1. A ferramenta instala essas tabelas durante a [migração de dados](https://devdocs.magento.com/guides/v2.3/migration/migration-migrate-data.html) (na documentação do desenvolvedor), bem como os disparadores de banco de dados que controlam alterações e preenchem tabelas de exclusão.

Um motivo para o erro pode ser que você esteja tentando migrar de uma *cópia* do seu armazenamento do Live Adobe Commerce 1, não do próprio armazenamento do Live. Quando você faz uma cópia de um armazenamento Adobe Commerce 1 em tempo real que nunca foi migrado, a cópia não contém os acionadores e as tabelas deltalog adicionais necessárias para concluir uma migração delta. Portanto, a migração falha. A Ferramenta de migração de dados NÃO faz comparações entre o BD de AC1 e AC2 para migrar as diferenças. Em vez disso, a ferramenta usa os acionadores e as tabelas de exclusão instaladas durante a primeira migração para executar as migrações delta subsequentes. Nesse caso, sua cópia do banco de dados Adobe Commerce 1 ativo não conterá os acionadores e as tabelas de exclusão que a Ferramenta de migração de dados usa para executar uma migração.

### Possível solução

Recomendamos testar o processo de migração de uma cópia do banco de dados do Adobe Commerce 1 para corrigir seus problemas de migração. Depois de corrigir os problemas na cópia, inicie o processo de migração novamente a partir do banco de dados Adobe Commerce 1 em tempo real. Isso ajudará a garantir um processo de migração tranquilo.

## Leitura relacionada

[Práticas recomendadas para modificar tabelas de banco de dados](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) no Manual de implementação do Commerce
