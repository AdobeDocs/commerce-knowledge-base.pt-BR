---
title: Solução de problemas da Ferramenta de migração de dados
description: Este artigo fornece soluções para erros que podem ocorrer ao executar a Ferramenta de migração de dados.
exl-id: 9beb31ae-ed3c-42e1-b0bf-33fb1c91e0ea
feature: Data Import/Export
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '727'
ht-degree: 0%

---

# Solução de problemas da Ferramenta de migração de dados

Este artigo fornece soluções para erros que podem ocorrer ao executar a Ferramenta de migração de dados.

## Documentos/campos de origem não mapeados {#source-documents-fields-not-mapped}

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

Esta mensagem é exibida porque a Ferramenta de migração de dados executa testes internos para verificar se as tabelas e os campos são consistentes entre *origem* (Adobe Commerce 1) e *destino* (Adobe Commerce 2).

### Possíveis soluções

* Instale as extensões correspondentes do Adobe Commerce 2 de [Commerce Marketplace](https://marketplace.magento.com/).     Se os dados conflitantes forem originários de uma extensão que adiciona elementos de estrutura de banco de dados próprios, a versão Adobe Commerce 2 da mesma extensão poderá adicionar esses elementos ao banco de dados de destino (Adobe Commerce 2), corrigindo o problema.
* Use o `-a` argumento ao executar a ferramenta para resolver erros automaticamente e impedir que a migração pare.
* Configure a Ferramenta para ignorar os dados problemáticos.

Para ignorar entidades de banco de dados, adicione o `<ignore>` para uma entidade na `map.xml` arquivo, desta forma:

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
>Antes de ignorar entidades pelo arquivo de mapa ou usando o `-a` , certifique-se de que não precisa dos dados afetados no armazenamento do Adobe Commerce 2.

## A classe não está mapeada no registro {#class-does-not-exist-but-mentioned}

### Mensagem de erro

```bash
Class <extension/class_name> is not mapped in record <attribute_id=196>
```

### Causa

Não foi possível encontrar uma classe da base de código do Adobe Commerce 1 na base de código do Adobe Commerce 2 durante a [Etapa de migração do EAV](https://devdocs.magento.com/guides/v2.3/migration/migration-tool-internal-spec.html#eav) na documentação do desenvolvedor. Na maioria dos casos, a classe ausente pertence a um [extensão](https://glossary.magento.com/extension).

### Possíveis soluções

* Instale a extensão correspondente do Adobe Commerce 2.
* Ignore o atributo que causa o problema.    Para isso, adicione o atributo à variável `ignore` grupo no `eav-attribute-groups.xml.dist` arquivo.
* Adicionar mapeamento de classe usando o `class-map.xml.dist` arquivo.

## Falha na restrição de chave estrangeira

### Texto da mensagem de erro

```bash
Foreign key <KEY_NAME> constraint fails on source database. Orphan records id: <id_1>, <id_2> from <child_table>.<field_id> has no referenced records in <parent_table>
```

### Causa

Há registros de banco de dados ausentes no `parent_table` para o qual o `field_id` do `child_table` aponta para.

### Possível solução

Excluir os registros de `child_table` , se você não precisar deles.

Para manter os registros, desative a variável `Data Integrity Step` modificando as ferramentas de migração de dados `config.xml` .

## Duplicatas em regravações de URL

```xml
There are duplicates in URL rewrites:
Request path: towel.html Store ID: 2 Target path: catalog/product/view/id/10
Request path: towel.html Store ID: 2 Target path: catalog/product/view/id/12
```

### Causa

A variável `Target path` em uma reescrita de URL deve ser especificado por um par exclusivo de `Request path` + `Store ID` . Este erro relata duas entradas que usam a mesma `Request path` + `Store ID` emparelhar com dois `Target path` valores.

### Possível solução

Ativar o `auto_resolve_urlrewrite_duplicates` opção no seu `config.xml` arquivo.

Essa configuração adiciona uma sequência de hash aos registros conflitantes de [URL](https://glossary.magento.com/url) substitui e mostra o resultado da resolução na interface da linha de comando.

## Incompatibilidade de entidades {#mismatch-of-entities}

### Mensagem de erro

```bash
Mismatch of entities in the document: <DOCUMENT> Source: <COUNT_ITEMS_IN_SOURCE_TABLE> Destination: <COUNT_ITEMS_IN_DESTINATION_TABLE>
```

### Causa

O erro ocorre durante a etapa de verificação de volume. Isso significa que a contagem de registros do banco de dados do Adobe Commerce 2 do documento não é a mesma que no Adobe Commerce 1.

Os registros ausentes ocorrem quando um cliente faz um pedido durante a migração.

### Possível solução

Execute a Ferramenta de migração de dados no `Delta` para transferir alterações incrementais.

## O Deltalog não está instalado {#deltalog-is-not-installed}

### Mensagem de erro

```bash
Deltalog for <TABLE_NAME> is not installed
```

### Causa

Esse erro ocorre durante [migração incremental](https://devdocs.magento.com/guides/v2.3/migration/migration-migrate-delta.html) (em nossa documentação do desenvolvedor) de alterações nos dados. Significa tabelas de exclusão (com prefixo `m2_cl_*`) não foram encontrados no banco de dados do Adobe Commerce 1. A ferramenta instala essas tabelas durante [migração de dados](https://devdocs.magento.com/guides/v2.3/migration/migration-migrate-data.html) (na documentação do desenvolvedor) e acionadores de banco de dados que rastreiam alterações e preenchem tabelas de exclusão.

Um motivo para o erro pode ser que você esteja tentando migrar de um *copiar* da sua loja Adobe Commerce 1 ao vivo, não da própria loja. Quando você faz uma cópia de um armazenamento Adobe Commerce 1 em tempo real que nunca foi migrado, a cópia não contém os acionadores e as tabelas deltalog adicionais necessárias para concluir uma migração delta. Portanto, a migração falha. A Ferramenta de migração de dados NÃO faz comparações entre o BD de AC1 e AC2 para migrar as diferenças. Em vez disso, a ferramenta usa os acionadores e as tabelas de exclusão instaladas durante a primeira migração para executar as migrações delta subsequentes. Nesse caso, sua cópia do banco de dados Adobe Commerce 1 ativo não conterá os acionadores e as tabelas de exclusão que a Ferramenta de migração de dados usa para executar uma migração.

### Possível solução

Recomendamos testar o processo de migração de uma cópia do banco de dados do Adobe Commerce 1 para corrigir seus problemas de migração. Depois de corrigir os problemas na cópia, inicie o processo de migração novamente a partir do banco de dados Adobe Commerce 1 em tempo real. Isso ajudará a garantir um processo de migração tranquilo.
