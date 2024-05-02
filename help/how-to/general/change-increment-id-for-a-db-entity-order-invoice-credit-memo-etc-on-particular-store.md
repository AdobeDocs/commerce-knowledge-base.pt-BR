---
title: Alterar ID de incremento de uma entidade do BD (pedido, fatura, aviso de crédito etc.) em uma loja específica
description: Este artigo discute como alterar a ID de incremento de uma entidade de banco de dados (BD) do Adobe Commerce (pedido, fatura, aviso de crédito etc.) em um armazenamento Adobe Commerce específico usando a instrução SQL "ALTER TABLE".
exl-id: 3704dd97-3639-44dc-9b8b-cf09f0c04e6c
feature: Invoices
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 0%

---

# Alterar ID de incremento de uma entidade do BD (pedido, fatura, aviso de crédito etc.) em uma loja específica

Este artigo discute como alterar a ID de incremento de uma entidade de banco de dados (BD) do Adobe Commerce (pedido, fatura, aviso de crédito etc.) em uma loja específica do Adobe Commerce usando o `ALTER TABLE` Instrução SQL.

## Versões afetadas

* Adobe Commerce no local: 2.x.x
* Infraestrutura do Adobe Commerce na nuvem: 2.x.x
* MySQL: any [versão compatível](https://devdocs.magento.com/guides/v2.2/install-gde/system-requirements-tech.html#database)

## Quando você precisaria alterar a ID de incremento (ocorrências)

Talvez seja necessário alterar a ID de incremento para novas entidades de BD nestes casos:

* Após uma restauração de backup rígido em um site ativo
* Alguns registros de pedidos foram perdidos, mas suas IDs já estão sendo usadas por gateways de pagamento (como PayPal) para sua conta de Comerciante atual. Sendo assim, os gateways de pagamento param de processar novos pedidos que têm as mesmas IDs, retornando o erro &quot;ID de fatura duplicada&quot;

>[!NOTE]
>
>Você também pode corrigir o problema do gateway de pagamento para PayPal, permitindo vários pagamentos por ID de fatura nas Preferências de Recebimento de Pagamento do PayPal. Consulte [Solicitação rejeitada do gateway do PayPal - problema de fatura duplicado](/help/troubleshooting/payments/paypal-gateway-rejected-request-duplicate-invoice-issue.md) em nossa base de conhecimento de suporte.

## Etapas de pré-requisito

1. Localize lojas e entidades para as quais a nova ID de incremento deve ser alterada.
1. [Conectar](https://devdocs.magento.com/guides/v2.2/install-gde/prereq/mysql_remote.html) para seu banco de dados MySQL. Para o Adobe Commerce na infraestrutura em nuvem, no início, é necessário [SSH para o seu ambiente](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html).
1. Verifique o valor de auto\_increment atual para a tabela de sequência de entidade usando a seguinte query:

```sql
SHOW TABLE STATUS FROM `{database_name}` WHERE `name` LIKE 'sequence_{entity_type}_{store_id}';
```

### Exemplo

Se estiver verificando um incremento automático para um pedido na loja com *ID=1*, o nome da tabela seria:

```sql
'sequence_order_1'
```

Se o valor de `auto_increment` a coluna é *1234*, o próximo pedido feito na loja com *ID=1* terá o *ID \#100001234*.

### Documentação relacionada

* [Configurar uma conexão remota com o banco de dados MySQL](https://devdocs.magento.com/guides/v2.2/install-gde/prereq/mysql_remote.html) na documentação do desenvolvedor.

## Atualizar entidade para alterar ID de incremento

Atualize a entidade usando a seguinte consulta:

```sql
ALTER TABLE sequence_{entity_type}_{store_id} AUTO_INCREMENT = {new_increment_value};
```

>[!WARNING]
>
>Importante: o novo valor de incremento deve ser maior que o atual, não menor!

### Exemplo

Após executar a seguinte query:

```sql
ALTER TABLE sequence_order_1 AUTO_INCREMENT = 2000;
```

o próximo pedido feito na loja com *ID=1* terá o *ID \#100002000*.

## Etapas adicionais recomendadas para o ambiente de produção (Nuvem)

Antes de executar o `ALTER TABLE` no ambiente de produção do Adobe Commerce na infraestrutura em nuvem, recomendamos executar estas etapas:

* Teste todo o procedimento de alteração da ID de incremento no ambiente de preparo
* [Criar](/help/how-to/general/create-database-dump-on-cloud.md) um backup de BD para restaurar seu BD de produção em caso de falha

## Documentação relacionada

* [Criar despejo de banco de dados na nuvem](/help/how-to/general/create-database-dump-on-cloud.md) em nossa base de conhecimento de suporte.
* [SSH para o seu ambiente](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html) na documentação do desenvolvedor.
