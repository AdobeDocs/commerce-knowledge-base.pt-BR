---
title: As alterações nas categorias não estão sendo salvas
description: Este artigo fornece uma correção para, ao atualizar categorias de produto por meio do Administrador do Commerce, as alterações não são exibidas no Administrador e na loja. O problema é causado pelos dados corrompidos na tabela "catalog_category_entity". Para resolver o problema, corrija ou remova os registros de atualização de categoria problemáticos na tabela. Depois disso, você poderá atualizar as categorias de produto usando o Administrador.
exl-id: d951205c-add9-478c-9c7d-2ba975d53b14
feature: Categories
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '721'
ht-degree: 0%

---

# As alterações nas categorias não estão sendo salvas

Este artigo fornece uma correção para, ao atualizar categorias de produto por meio do Administrador do Commerce, as alterações não são exibidas no Administrador e na loja. O problema é causado pelos dados corrompidos na tabela `catalog_category_entity`. Para resolver o problema, corrija ou remova os registros de atualização de categoria problemáticos na tabela. Depois disso, você poderá atualizar as categorias de produto usando o Administrador.

## Problema

Depois de fazer alterações em uma categoria de produto no Administrador e salvar, as novas atualizações não são salvas nem exibidas no Administrador e na loja.

### Etapas a serem reproduzidas

1. Ir para **Catálogo** > **Categorias**.
1. Selecione uma categoria.
1. Faça as alterações e clique em **Salvar**.
1. Mensagem exibida: *Você salvou a categoria*.
1. Observe que a alteração que você fez não foi salva.

## Causa possível: dados corrompidos na tabela `catalog_category_entity`

O problema é causado pelos mesmos valores na coluna `created_in` dos registros de categoria afetados no banco de dados.

![Dados corrompidos na tabela catalog_category_entity](assets/catalog_category_entity.png)

Detalhes:

* A tabela do banco de dados `catalog_category_entity` tem dois ou mais registros para a categoria afetada (esses registros têm o mesmo valor `entity_id`).
* Estes registros de categoria têm **os mesmos valores na `created_in` coluna**.

### Como a segunda entrada do BD (e todas as próximas) aparece no BD para uma mesma categoria?

O segundo registro de DB (e, possivelmente, os próximos) para a categoria afetada significa que houve atualizações de categoria programadas usando o módulo Magento\_Staging. O módulo cria um registro adicional para uma categoria no `catalog_category_entity` e esse é o comportamento esperado do aplicativo; o problema é que os registros têm os mesmos valores para a coluna `created_in`.

### Como os mesmos valores são exibidos?

Não podemos expor os motivos da corrupção de dados com certeza. As possíveis razões podem incluir:

* personalizações (código, temas etc.)
* migração de dados incorreta
* restauração de dados incorreta a partir do backup

Pelo que sabemos, essa corrupção de dados não é típica da instância do Adobe Commerce &quot;limpa&quot; (pronta para uso) e não pode ser reproduzida em uma instalação do Adobe Commerce sem personalizações.

### Como verificar se esse é o seu problema

A tabela `catalog_category_entity` deve ter vários registros para a categoria afetada (os registros devem ter o mesmo valor `entity_id`) e pelo menos dois desses registros devem ter os mesmos valores `created_in`. Com isso, as atualizações agendadas para Preparo não seriam exibidas no Administrador do Commerce; você só veria o bloco vazio de Alterações agendadas.

#### Etapas a serem verificadas

1. Acesse a tabela catalog\_category\_entity no banco de dados.
1. Filtre entidades por entity\_id, com entity\_id identificando a categoria afetada.
1. Se os valores na coluna criada\_em forem os mesmos para entradas diferentes com a mesma entity\_id, esse é o nosso caso. Normalmente, os valores de `created_in` são diferentes para cada registro.

![Dados corrompidos na tabela catalog_category_entity](assets/catalog_category_entity.png)

## Solução

Você pode escolher uma das seguintes soluções:

1. **Excluir** os registros de atualização de categoria problemáticos
1. **Reparar** os registros de atualização de categoria problemáticos

### Excluir os registros de atualização de categoria problemáticos

Nesta solução, será necessário definir o valor `updated_in` correto para o registro de categoria inicial e excluir todos os outros registros para esta categoria. Isso remove todas as atualizações de categoria programadas.

Siga estas etapas:

1. Localize os registros de BD com o `entity_id` da categoria afetada.
1. Selecione o registro com o maior inteiro na coluna `updated_in`.
1. Copie o valor `updated_in` do registro selecionado.
1. Selecione o registro com `row_id` = `entity_id` (registro de categoria inicial) e cole o valor copiado na coluna `updated_in` desse registro.
1. Excluir linha(s) com `row_id` diferente de `entity_id`.

### Reparar os registros de atualização de categoria problemáticos

1. Localize os registros de categoria com o mesmo `entity_id` e o mesmo valor `created_in`.
1. Selecione o registro em que `row_id` = `entity_id` e copie o valor `updated_in`.
1. Selecione o registro em que `row_id` não é igual a `entity_id` e cole o valor `updated_in` copiado como o valor `created_in`. Consulte a captura de tela abaixo como uma ilustração.    ![Copiando created_in value.png](assets/copy_created-in_value.png)
1. Verifique se o registro de atualização de categoria, cujo valor `created_in` você atualizou (na etapa 3), existe na tabela `staging_update`. *Por exemplo:* SE o valor `created_in` copiado for 1509281953, a entidade com `row_id` = 1509281953 deverá existir na tabela `staging_update`
