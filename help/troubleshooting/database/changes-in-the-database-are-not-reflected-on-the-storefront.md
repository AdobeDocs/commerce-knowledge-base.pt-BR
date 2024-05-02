---
title: As alterações no banco de dados não são refletidas na loja
description: Este artigo fornece soluções para evitar atrasos ou interrupções nas atualizações de entidade que estão sendo aplicadas. Isso inclui como evitar que tabelas de log de alterações fiquem superdimensionadas e como configurar acionadores da tabela MySQL.
exl-id: ac52c808-299f-4d08-902f-f87db1fa7ca6
feature: Catalog Management, Categories, Services, Storefront
role: Developer
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '543'
ht-degree: 0%

---

# As alterações no banco de dados não são refletidas na loja

Este artigo fornece soluções para evitar atrasos ou interrupções nas atualizações de entidade que estão sendo aplicadas. Isso inclui como evitar que tabelas de log de alterações fiquem superdimensionadas e como configurar acionadores da tabela MySQL.

Produtos e versões afetados:

* Adobe Commerce na infraestrutura em nuvem 2.2.x, 2.3.x
* Adobe Commerce no local 2.2.x, 2.3.x

## Problema

As alterações feitas no banco de dados não são refletidas na loja ou há um atraso significativo na aplicação das atualizações de entidade. As entidades que podem ser afetadas incluem produtos, categorias, preços, estoque, regras de catálogo, regras de vendas e regras de meta.

## Causa

Se seus indexadores estiverem [configurado para atualizar por agendamento](https://devdocs.magento.com/guides/v2.3/config-guide/cli/config-cli-subcommands-index.html#configure-indexers), o problema pode ser causado por uma ou mais tabelas com logs de alteração muito grandes ou acionadores MySQL não configurados.

### Tabelas de log de alterações superdimensionadas

As tabelas de log de alterações se tornarão tão grandes se a variável `indexer_update_all_views` o trabalho cron não foi concluído várias vezes com êxito.

As tabelas de log de alterações são as tabelas de banco de dados nas quais as alterações nas entidades são rastreadas. Um registro é armazenado em uma tabela de log de alterações desde que a alteração não seja aplicada, o que é executado pelo `indexer_update_all_views` trabalho cron. Há várias tabelas de log de alterações em um banco de dados Adobe Commerce, que são nomeadas de acordo com o seguinte padrão: INDEXER\_TABLE\_NAME + ‘\_cl’, por exemplo `catalog_category_product_cl`, `catalog_product_category_cl`. Você pode encontrar mais detalhes sobre como as alterações são rastreadas no banco de dados na [Visão geral da indexação > Visualizar](https://devdocs.magento.com/guides/v2.3/extension-dev-guide/indexing.html#m2devgde-mview) artigo em nossa documentação para desenvolvedores.

### Acionadores do banco de dados MySQL não configurados

Você suspeitaria que os acionadores do banco de dados não estivessem sendo configurados se, após adicionar ou alterar uma entidade (produto, categoria, regra de destino e assim por diante), nenhum registro fosse adicionado à tabela de log de alteração correspondente.

## Solução

>[!WARNING]
>
>É altamente recomendável criar um backup de banco de dados antes de executar qualquer manipulação e evitá-la durante períodos de carregamento de site alto.

### Evitar que as tabelas de log de alterações sejam superdimensionadas

Certifique-se de que o `indexer_update_all_views` o trabalho cron é sempre concluído com sucesso.

Você pode usar a seguinte consulta SQL para obter todas as instâncias com falha da `indexer_update_all_views` trabalho cron:

```sql
select * from cron_schedule where job_code = "indexer_update_all_views" and status
  <> "success" and status <> "pending";
```

Ou você pode verificar seu status nos logs procurando pelo `indexer_update_all_views` entradas:

* `<install_directory>/var/log/cron.log` - para as versões 2.3.1+ e 2.2.8+
* `<install_directory>/var/log/system.log` - para versões anteriores

### Redefinir acionadores da tabela MySQL

Para configurar os acionadores ausentes da tabela do MySQL, é necessário redefinir o modo indexador:

1. Alterne para &#39;Ao salvar&#39;.
1. Volte para &#39;Em programação&#39;.

Use o seguinte comando para executar esta operação.

>[!WARNING]
>
>Antes de alternar os modos do indexador, recomendamos colocar seu site no [manutenção](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/setup/application-modes.html#maintenance-mode) e [desabilitar trabalhos cron](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html#disable-cron-jobs) para evitar bloqueios de banco de dados.

```bash
php bin/magento indexer:set-mode {realtime|schedule} [indexerName]
```

>[!INFO]
>
>Os gatilhos de banco de dados relacionados a indexadores são adicionados quando o modo indexador está definido como agendado e removidos quando o modo indexador está definido como em tempo real. Se os acionadores estiverem ausentes no banco de dados enquanto os indexadores estiverem definidos como programados, altere os indexadores para tempo real e altere-os de volta para programados. Isso redefine os acionadores.

## Leitura relacionada

<ul><li title="As tabelas MySQL são muito grandes"><a href="/help/troubleshooting/database/mysql-tables-are-too-large.md">As tabelas MySQL são muito grandes</a> em nossa base de conhecimento de suporte.</li>
<li title="As tabelas MySQL são muito grandes"><a href="https://devdocs.magento.com/guides/v2.3/extension-dev-guide/indexing.html#m2devgde-mview">Visão geral do indexador &gt; Visualizar</a> na documentação do desenvolvedor.</li></ul>
