---
title: Erro 404 em todas as páginas devido ao problema de preparo de conteúdo
description: Este artigo fornece uma correção para o problema do Adobe Commerce no local e do Adobe Commerce na infraestrutura em nuvem, em que você recebe um erro 404 ao acessar qualquer página da loja ou o administrador do Commerce.
exl-id: 62d8ba6e-8550-4e1e-8e8d-8f319c92778a
feature: CMS, Catalog Management, Categories, Page Content, Staging
role: Developer
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '528'
ht-degree: 0%

---

# Erro 404 em todas as páginas devido ao problema de preparo de conteúdo

Este artigo fornece uma correção para o problema do Adobe Commerce no local e do Adobe Commerce na infraestrutura em nuvem, em que você recebe um erro 404 ao acessar qualquer página da loja ou o administrador do Commerce.

## Produtos e versões afetados

* Adobe Commerce no local 2.2.x, 2.3.x
* Adobe Commerce na infraestrutura em nuvem 2.2.x, 2.3.x

## Problema

>[!NOTE]
>
>Este artigo não se aplica à situação em que você recebe um erro 404 ao tentar [pré-visualizar a atualização de preparo](https://docs.magento.com/user-guide/cms/content-staging-scheduled-update.html#preview-the-scheduled-change). Se você encontrar esse problema, abra um [tíquete de suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

O acesso a qualquer página da loja ou ao Administrador resulta no erro 404 (a página &quot;Ops, nossa má...&quot;) após executar operações com atualizações programadas para ativos de conteúdo da loja usando [Preparo de conteúdo](https://experienceleague.adobe.com/docs/commerce-admin/content-design/staging/content-staging.html) (atualizações para ativos de conteúdo de armazenamento agendadas usando o [Magento\_Módulo de preparo](https://developer.adobe.com/commerce/php/module-reference/)). Por exemplo, você pode ter excluído um Produto com uma atualização programada ou removido a data final da atualização programada.

Um ativo de conteúdo de armazenamento inclui:

* Produto
* Categoria
* Regra de preço de catálogo
* Regra de preço do carrinho
* Página CMS
* Bloco CMS
* Widget

Alguns cenários são discutidos na seção Causa abaixo.

## Causa

A variável `flag` A tabela no banco de dados (DB) contém links inválidos para a variável `staging_update` tabela.

O problema está relacionado ao preparo de conteúdo. Abaixo estão dois cenários específicos; observe que pode haver mais situações que acionam o problema.

**Cenário 1:** Excluindo um ativo de conteúdo de armazenamento que:

* tem uma atualização agendada com o Preparo de conteúdo
* a atualização tem uma data final (ou seja, a data de expiração após a qual o ativo atualizado reverte para a versão anterior)
* a data final da atualização está no passado

Ao mesmo tempo, o problema pode não ocorrer se um ativo excluído não tiver uma data final para a atualização agendada.

**Cenário 2:** Removendo a data/hora final de uma atualização agendada.

### Identificar se o problema está relacionado

Para identificar se o problema que você está enfrentando é o descrito neste artigo, execute a seguinte consulta de BD:

```sql
   SELECT f.flag_data >'$.current_version' as flag_version, (su.id IS NOT NULL) as update_exists
   -> FROM flag f
   -> LEFT JOIN staging_update su
   -> ON su.id = f.flag_data >'$.current_version'
   -> WHERE flag_code = 'staging';
```

Se a consulta retornar uma tabela em que `update_exists` é &quot;0&quot;, então um link inválido para a variável `staging_update` existe no banco de dados e as etapas descritas na seção [Seção Solução](#solution) O ajudará a resolver o problema. Veja a seguir um exemplo do resultado da query com `update_exists` valor igual a &quot;0&quot;:

![update_exists_0.png](assets/update_exists_0.png)

Se a consulta retornar uma tabela em que `update_exists` for &quot;1&quot; ou um resultado vazio, significa que o problema não está relacionado às atualizações de preparo. Veja a seguir um exemplo do resultado da query com `update_exists` valor igual a &quot;1&quot;:

![updates_exist_1.png](assets/updates_exist_1.png)

Nesse caso, você pode consultar a [Solução de problemas de site inativo](/help/troubleshooting/site-down-or-unresponsive/magento-site-down-troubleshooter.md) para obter ideias de solução de problemas.

## Solução

1. Execute a seguinte consulta para excluir o link inválido para o `staging_update` tabela:

   ```sql
   DELETE FROM flag WHERE flag_code = 'staging';
   ```

1. Aguarde a execução do trabalho cron (é executado em até cinco minutos, se configurado corretamente) ou execute-o manualmente, se você não tiver o cron configurado.

O problema deve ser resolvido logo após a correção do link inválido. Se o problema persistir, [enviar um tíquete de suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).
