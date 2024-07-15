---
title: Há várias linhas no banco de dados para a mesma entidade
description: Este artigo fornece uma solução para o problema em que há várias linhas para a mesma ID de entidade no banco de dados.
feature: Catalog Management, Categories, Services, Storefront
role: Developer
exl-id: 09d5c321-9c45-4041-b6f6-831efca0977e
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 0%

---

# Várias linhas no banco de dados para a mesma entidade

Este artigo fornece uma solução para o problema em que há várias linhas para a mesma ID de entidade no banco de dados.

## Produtos e versões afetados:

* Adobe Commerce (todas as versões)

## Problema

Há várias linhas para a mesma ID de entidade no banco de dados.

Por exemplo, depois de receber uma lista de registros com IDs de entidade duplicadas, ao executar esta consulta:

```
SELECT * FROM $entityTable WHERE $column = <$entityID> ORDER BY created_in;
```

Onde `$entityID = ID` da página de categoria/produto/regra de preço do carrinho/regra de preço do catálogo/CMS.

| Entidade | $entityTable | $coluna |
|------------------|-----------------------------------|------------------|
| Categoria/produto | catalog_category_entity/catalog_product_entity | entity_id |
| Regra de Preço do Carrinho/Regra de Preço do Catálogo | salesrule/catálogo | rule_id |
| Página CMS | cms_page | page_id |

## Causa

Esse é o comportamento esperado. As várias linhas são criadas pela funcionalidade Preparo de conteúdo:

* Se você especificar uma data de início sem uma data de término, haverá pelo menos duas linhas com a mesma entidade/regra/ID de página. Uma linha indicará o estado original da entidade (a linha em que `created_in=1`), e uma linha indicará o *Fim da Atualização Agendada*.

* Se você especificar uma data de início com uma data de término, haverá pelo menos três linhas com a mesma entidade/regra/ID de página. Uma linha indicará o estado original da entidade (a linha em que `created_in=1`), uma linha será para o *Início da Atualização Agendada* e uma linha será para o *Fim da Atualização Agendada*.

Por exemplo, nesta consulta:

```
SELECT row_id, entity_id, created_in, updated_in FROM catalog_product_entity WHERE entity_id = 483 ORDER BY created_in;
```

![várias_linhas_no_banco_de_dados.png](assets/multiple_rows_in_database.png)

* Os valores `created_in` e `updated_in` devem seguir este padrão: O valor `created_in` da linha atual é igual ao valor `updated_in` na linha anterior. Além disso, a primeira linha deve conter `created_in = 1` e a última linha deve conter `updated_in = 2147483647`. (Se houver apenas uma linha, você deverá ver `created_in=1` e `updated_in=2147483647`).

### Por que a segunda entrada do BD (e todas as próximas) aparece no BD para a mesma entidade?

* O segundo registro de BD (e, possivelmente, os próximos) da entidade afetada significa que houve atualizações de Preparo de Conteúdo agendadas usando o módulo `Magento_Staging`, que faz um registro adicional para uma entidade nas respectivas tabelas.

Um problema só ocorrerá se os registros tiverem os mesmos valores para as colunas `created_in` ou `updated_in`.

## Solução

Esse é o comportamento esperado e só levará a problemas se houver discrepâncias entre as linhas.

## Leitura relacionada

* [As alterações nas categorias não estão sendo salvas](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/changes-to-categories-are-not-being-saved.html) em nossa base de dados de conhecimento de suporte.
* [Entradas duplicadas na tabela de catálogo após a edição da data final de uma atualização de agendamento](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/duplicate-entries-in-the-catalogrule-table-after-editing-the-end-date-of-a-schedule-update.html) em nossa base de dados de conhecimento de suporte.
