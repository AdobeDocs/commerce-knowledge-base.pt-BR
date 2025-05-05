---
title: O Elasticsearch 5 está configurado, mas a página de pesquisa não carrega com o erro "Fielddata is disabled..."
description: 'Este tópico descreve como corrigir o problema com o Elasticsearch 5, em que a página de pesquisa não carrega, e a exceção semelhante à seguinte é lançada:'
exl-id: f5fa8144-4e7c-45ce-89d0-a8367e91d6db
feature: Cache
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---

# O Elasticsearch 5 está configurado, mas a página de pesquisa não carrega com o erro &quot;Fielddata is disabled...&quot;

Este tópico descreve como corrigir o problema com o Elasticsearch 5, em que a página de pesquisa não carrega, e a exceção semelhante à seguinte é lançada:

```bash
{"0":"{\"error\":{\"root_cause\":[{\"type\":\"illegal_argument_exception\",\"reason\":\"Fielddata is disabled on text fields by default. Set fielddata=true on [%attribute_code%]] in order to load fielddata in memory by uninverting the inverted index. Note that this can however use significant memory.\"}].
```

## Versões afetadas

* Adobe Commerce 2.2.x
* Elasticsearch v.5

>[!NOTE]
>
>O Elasticsearch v.5 está obsoleto para o Adobe Commerce 2.3.x

## Problema

Pré-condições: o Elasticsearch 5 está configurado.

Na solicitação de pesquisa, a seguinte exceção é gerada nos logs:

```bash
{"0":"{\"error\":{\"root_cause\":[{\"type\":\"illegal_argument_exception\",\"reason\":\"Fielddata is disabled on text fields by default. Set fielddata=true on [%attribute_code%]] in order to load fielddata in memory by uninverting the inverted index. Note that this can however use significant memory.\"}].
```

## Causa

Por padrão, somente determinados tipos de atributos de produto podem ser usados na Navegação em camadas. Eles são Sim/Não, Lista suspensa, Seleção múltipla e Preço. É por isso que, no Administrador do Commerce, você não pode definir um atributo de nenhum outro tipo como **Usar na Navegação em Camadas** = *Filtrável* ou **Usar na Navegação em Camadas de Resultados da Pesquisa** = *Sim*. Mas há uma possibilidade técnica de contornar essa limitação alterando diretamente os valores `is_filterable` e `is_filterable_in_search` no banco de dados. Se isso acontecer e qualquer outro tipo de atributo, como Data, Texto, etc., for definido para ser usado na Navegação em camadas, o Elasticsearch 5 acionará uma exceção.

Para garantir que esse seja o caso, você precisa descobrir se há algum outro atributo diferente de Suspenso, Seleção múltipla e Preço que estejam definidos para serem usados na Navegação em camadas. Execute a seguinte consulta para procurar esses atributos:

```sql
SELECT ea.attribute_code, ea.frontend_input, cea.is_filterable, cea.is_filterable_in_search FROM eav_attribute AS ea
    -> INNER JOIN catalog_eav_attribute AS cea ON ea.attribute_id = cea.`attribute_id`
    -> WHERE (is_filterable = 1 OR is_filterable_in_search = 1) AND frontend_input NOT IN ('boolean', 'multiselect', 'select', 'price');
```

O resultado conterá uma lista de atributos usados para a Navegação em camadas, cujo tipo não permite isso. Siga as etapas descritas na seção a seguir para corrigir isso.

## Solução

Para corrigir o problema, você precisa definir `is_filterable` (ou seja, usado na Navegação em Camadas) e `filterable_in_search` (ou seja, usado na Navegação em Camadas dos resultados da pesquisa) como &quot;0&quot; (não usado). Para fazer isso, siga estas etapas:

1. Criar um backup de banco de dados.
1. Use uma ferramenta de banco de dados como [phpMyAdmin](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/installation-guide/prerequisites/optional-software#phpmyadmin) ou acesse o BD manualmente a partir da linha de comando para executar a seguinte consulta SQL:

   ```sql
   UPDATE catalog_eav_attribute AS cea
       INNER JOIN eav_attribute AS ea
           ON ea.attribute_id = cea.attribute_id
   SET cea.is_filterable = 0, cea.is_filterable_in_search = 0
   WHERE (cea.is_filterable = 1 OR cea.is_filterable_in_search = 1)
       AND frontend_input NOT IN ('boolean', 'multiselect', 'select', 'price');
   ```

1. Execute a reindexação completa da Pesquisa no catálogo usando o seguinte comando:

   ```bash
   bin/magento indexer:reindex catalogsearch_fulltext
   ```

1. Limpar cache executando

   ```bash
   bin/magento cache:clean
   ```

ou no Administrador do Commerce em **Sistema** > **Ferramentas** > **Gerenciamento de Cache**.

Agora você pode realizar pesquisas em catálogos sem problemas.
