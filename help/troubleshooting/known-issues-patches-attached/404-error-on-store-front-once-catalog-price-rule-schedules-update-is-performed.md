---
title: 404 Erro na loja assim que a atualização das programações de regra de preço de catálogo é executada
description: Este artigo fornece um patch e as etapas necessárias para corrigir o problema conhecido do Adobe Commerce 2.2.1 relacionado à obtenção de um erro 404 em todas as páginas iniciais da loja, depois que uma atualização de regra de preço de catálogo foi criada e sua hora de início foi editada posteriormente. Para corrigir o problema, você precisa aplicar o patch.
exl-id: 7ea148a5-56cb-479a-8b2f-fae8b3bd4b22
feature: Cache, Catalog Management, Marketing Tools, Orders, Price Rules
role: Developer
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '711'
ht-degree: 0%

---

# 404 Erro na loja assim que a atualização das programações de regra de preço de catálogo é executada

Este artigo fornece um patch e as etapas necessárias para corrigir o problema conhecido do Adobe Commerce 2.2.1 relacionado à obtenção de um erro 404 em todas as páginas iniciais da loja, depois que uma atualização de regra de preço de catálogo foi criada e sua hora de início foi editada posteriormente. Para corrigir o problema, você precisa aplicar o patch.

## Problema

As páginas da vitrine eletrônica ficam indisponíveis, retornando o erro 404. O problema ocorre depois que a atualização da regra de preço do catálogo ativo vence, contanto que a data inicial desta atualização tenha sido editada após a criação inicial.

<u>Etapas a serem reproduzidas</u>:

1. No Administrador do Commerce, crie uma nova Regra de preço de catálogo em **Marketing** > **Promoções** > **Regra de preço de catálogo**.
1. Na grade **Regra de Preço do Catálogo**, clique em **Editar,** agendar uma nova Atualização e definir o **Status** como *Ativo.*
1. Navegue até **Conteúdo** > **Estágios de Conteúdo** > **Painel.**
1. Selecione a atualização criada recentemente e altere sua hora inicial.
1. Salve as alterações.

<u>Resultado esperado</u>:

Quando a data inicial de Atualização se torna efetiva, a regra de preço de catálogo é aplicada com sucesso.

<u>Resultado real</u>:

Quando a data de início da Atualização entrar em vigor, todos os catálogos e produtos da loja ficarão indisponíveis, retornando o erro 404.

## Solução

Para restaurar páginas de catálogo e usar totalmente a funcionalidade de atualizações de regras de preço de catálogo, é necessário instalar o patch, excluir a regra manualmente e no administrador e corrigir os links inválidos no banco de dados. Você também precisará recriar a regra de preço do catálogo.

Veja a seguir uma descrição detalhada das etapas necessárias:

1. [Aplicar o patch](#patch).
1. No Administrador do Commerce, exclua a regra de preço do catálogo relacionada ao problema (em que a hora de início foi atualizada). Para fazer isso, abra a página de regras em **Marketing** > **Promoções** > **Regra de Preço de Catálogo** e clique em **Excluir Regra**.
1. O acesso ao banco de dados exclui manualmente o registro relacionado da tabela `catalogrule`.
1. Corrija os links inválidos no banco de dados. Consulte o [parágrafo relacionado](#fix_links) para obter detalhes.
1. No Administrador do Commerce em **Marketing**, vá para **Promoções** > **Regra de preço de catálogo** e crie a nova regra com a configuração necessária.
1. Limpe o cache do navegador em **Sistema** > **Gerenciamento de Cache**.
1. Verifique se os trabalhos cron estão configurados corretamente e podem ser executados com êxito.

## Correção {#patch}

O patch está anexado a este artigo. Para baixá-lo, role para baixo até o final do artigo e clique no nome do arquivo ou clique no link a seguir:

[Baixar MDVA-7392\_EE\_2.2.1\_COMPOSER\_v2.patch](assets/MDVA-7392_EE_2.2.1_COMPOSER_v2.patch.zip)

## Versões compatíveis do Adobe Commerce:

A correção foi criada para:

* Adobe Commerce 2.2.1

O patch também é compatível (mas pode não resolver o problema) com as seguintes versões e edições do Adobe Commerce:

* Adobe Commerce na infraestrutura em nuvem 2.2.0 - 2.2.4
* Adobe Commerce no local 2.2.0 e 2.2.2 - 2.2.4

## Como aplicar o patch

Para instruções, consulte [Como aplicar um patch de compositor fornecido por Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) em nossa base de dados de conhecimento de suporte.

## Corrigir os links inválidos para preparo no BD {#fix_links}

>[!WARNING]
>
>É altamente recomendável criar um backup de banco de dados antes de qualquer manipulação de banco de dados. Também recomendamos testar primeiro as consultas no ambiente de desenvolvimento.

Siga as etapas a seguir para corrigir as linhas com links inválidos para a tabela `staging_update`.

1. Verifique se os links inválidos para a tabela `staging_update` existem na tabela `flag`. Estes seriam registros onde `flag_code=staging`.
1. Identifique a versão inválida da tabela `flag` usando a seguinte consulta:

   ```sql
   SELECT flag_data FROM flag WHERE flag_code = 'staging';
   ```

1. Na tabela `staging_update`, selecione a versão existente que seja menor que a versão atual (inválida) e obtenha o valor da versão que seja dois números de volta. Você pode usá-la, não a versão anterior, para evitar a situação em que a versão anterior é a versão máxima na tabela `staging_update` que pode ser aplicada e ainda precisamos reaplicá-la.

   ```sql
   SELECT id FROM staging_update WHERE id < %current_id% ORDER BY id DESC LIMIT 1, 1
   ```

   A versão que você recebe em resposta é sua versão válida `id`.

1. Para as linhas com links inválidos na tabela `flag`, defina os valores de `flag_data` como dados que conterão uma ID de versão válida. Isso ajuda a salvar o desempenho na etapa de reindexação e permite evitar a reindexação de todas as entidades.

   ```sql
   UPDATE flag SET flag_data=REPLACE(flag_data, '%invalid_id%', '%new_valid_id%') WHERE flag_code='staging';
   ```

<u>Exemplo:</u>

```sql
SELECT flag_data FROM flag WHERE flag_code = 'staging'; <code class="language-bash">Response < 2.2 version</code>
```

```bash
+-------------------------------------------------+
```

```bash
| flag_data                                       |
```

```bash
+-------------------------------------------------+
```

```bash
| a:1:{s:15:"current_version";s:10:"1490005140";} |
```

```bash
+-------------------------------------------------+
```

```bash
Response from 2.2 version
```

```bash
+-------------------------------------------------+
```

```bash
| flag_data                                       |
```

```bash
+-------------------------------------------------+
```

```bash
| {"current_version":"1490005140"} |
```

```bash
+-------------------------------------------------+
```

```sql
SELECT id FROM staging_update WHERE id < 1490005140 <code class="language-sql">ORDER BY id DESC LIMIT 1, 1</code>;
```

```bash
Response:
```

```bash
1490005138
```

```sql
UPDATE flag SET flag_data=REPLACE(flag_data, '1490005140', '1490005138') WHERE flag_code='staging';
```

## Arquivos Anexados
