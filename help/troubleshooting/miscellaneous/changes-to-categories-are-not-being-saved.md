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

Este artigo fornece uma correção para, ao atualizar categorias de produto por meio do Administrador do Commerce, as alterações não são exibidas no Administrador e na loja. O problema é causado pelos dados corrompidos na `catalog_category_entity` tabela. Para resolver o problema, corrija ou remova os registros de atualização de categoria problemáticos na tabela. Depois disso, você poderá atualizar as categorias de produto usando o Administrador.

## Problema

Depois de fazer alterações em uma categoria de produto no Administrador e salvar, as novas atualizações não são salvas nem exibidas no Administrador e na loja.

### Etapas a serem reproduzidas

1. Ir para **Catálogo** > **Categorias**.
1. Selecione uma categoria.
1. Faça as alterações e clique em **Salvar**.
1. A mensagem é exibida: *Você salvou a categoria*.
1. Observe que a alteração que você fez não foi salva.

## Causa possível: dados corrompidos na `catalog_category_entity` tabela

O problema é causado pelos mesmos valores na variável `created_in` coluna dos registros de categoria afetados no banco de dados (DB).

![Dados corrompidos na tabela catalog_category_entity](assets/catalog_category_entity.png)

Detalhes:

* A variável `catalog_category_entity` A tabela do banco de dados tem dois ou mais registros para a categoria afetada (esses registros têm o mesmo `entity_id` valor).
* Esses registros de categoria têm **os mesmos valores na variável `created_in` coluna**.

### Como a segunda entrada do BD (e todas as próximas) aparece no BD para uma mesma categoria?

O segundo registro de DB (e, possivelmente, os próximos) para a categoria afetada significa que houve atualizações de categoria programadas usando o módulo Magento\_Staging. O módulo faz um registro adicional para uma categoria no `catalog_category_entity` e esse é o comportamento esperado do aplicativo; o problema é que os registros têm os mesmos valores para `created_in` coluna.

### Como os mesmos valores são exibidos?

Não podemos expor os motivos da corrupção de dados com certeza. As possíveis razões podem incluir:

* personalizações (código, temas etc.)
* migração de dados incorreta
* restauração de dados incorreta a partir do backup

Pelo que sabemos, essa corrupção de dados não é típica da instância do Adobe Commerce &quot;limpa&quot; (pronta para uso) e não pode ser reproduzida em uma instalação do Adobe Commerce sem personalizações.

### Como verificar se esse é o seu problema

A variável `catalog_category_entity` a tabela deve ter vários registros para a categoria afetada (os registros devem ter o mesmo `entity_id` pelo menos dois desses registros devem ter a mesma `created_in` valores. Com isso, as atualizações agendadas para Preparo não seriam exibidas no Administrador do Commerce; você só veria o bloco vazio de Alterações agendadas.

#### Etapas a serem verificadas

1. Acesse a tabela catalog\_category\_entity no banco de dados.
1. Filtre entidades por entity\_id, com entity\_id identificando a categoria afetada.
1. Se os valores na coluna criada\_em forem os mesmos para entradas diferentes com a mesma entity\_id, esse é o nosso caso. Normalmente, a variável `created_in` os valores são diferentes para cada registro.

![Dados corrompidos na tabela catalog_category_entity](assets/catalog_category_entity.png)

## Solução

Você pode escolher uma das seguintes soluções:

1. **Excluir** os registros de atualização de categoria problemáticos
1. **Reparar** os registros de atualização de categoria problemáticos

### Excluir os registros de atualização de categoria problemáticos

Nesta solução, será necessário definir as configurações corretas `updated_in` para o registro de categoria inicial e exclua todos os outros registros para essa categoria. Isso remove todas as atualizações de categoria programadas.

Siga estas etapas:

1. Localize os registros do BD com o `entity_id` da categoria afetada.
1. Selecione o registro com o maior número inteiro no `updated_in` coluna.
1. Copie o `updated_in` valor do registro selecionado.
1. Selecionar o registro com `row_id` = `entity_id` (registro de categoria inicial) e cole o valor copiado no `updated_in` deste registro.
1. Excluir linhas com `row_id` diferente de `entity_id` .

### Reparar os registros de atualização de categoria problemáticos

1. Localizar os registros de categoria com o mesmo `entity_id` e o mesmo `created_in` valor.
1. Selecione o registro onde `row_id` = `entity_id` e copie o `updated_in` valor.
1. Selecione o registro onde `row_id` não é igual a `entity_id` e cole a copiada `updated_in` value como o `created_in` valor. Consulte a captura de tela abaixo como uma ilustração.    ![Copiar o created_in value.png](assets/copy_created-in_value.png)
1. Verifique se o registro de atualização da categoria, a variável `created_in` valor que você atualizou (na etapa 3), existe na variável `staging_update` tabela. *Por exemplo:* SE a cópia `created_in` valor é 1509281953, ENTÃO a entidade com `row_id` = 1509281953 deve existir no `staging_update` tabela
