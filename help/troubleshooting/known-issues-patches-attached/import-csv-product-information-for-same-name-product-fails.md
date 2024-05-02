---
title: Falha ao importar informações de produto CSV para produto com o mesmo nome
description: Este artigo fornece uma correção para o problema conhecido do Adobe Commerce 2.2.3 relacionado à obtenção de erros ao tentar importar um arquivo `.csv` com informações de produtos se houver produtos com o mesmo nome.
exl-id: 420b0283-455a-4bd5-ba51-18f341ddacd5
feature: Data Import/Export, Products
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---

# Falha ao importar informações de produto CSV para produto com o mesmo nome

Este artigo fornece um patch para o problema conhecido do Adobe Commerce 2.2.3 relacionado à obtenção de erros ao tentar importar um `.csv` arquivo com informações de produtos se houver produtos com o mesmo nome.

## Problema

Quando um `.csv` for importado e houver produtos com o mesmo nome, você receberá o seguinte erro na etapa Verificar dados: *&quot;`URL Key XYZ was already generated for an item with the SKU %sku%"`*. O problema é causado pela regravação dos URLs dos produtos durante a importação, mesmo quando não há coluna para os URLs dos produtos na importação `.csv` arquivo.

<u>Etapas a serem reproduzidas</u>:

1. Crie dois produtos configuráveis com o mesmo nome no Administrador do Commerce.
1. Criar um `.csv` arquivo para importar dados para esses produtos, que tem, por exemplo, estas colunas: `sku` | `product_type` | `name` | `product_websites` | `store_view_code`
1. Ir para **Sistema** > **Transferência de dados** > **Importar** e selecione o `.csv` arquivo.
1. Clique em **Verificar dados**.

<u>Resultado esperado</u>:

Nenhum problema encontrado; você pode importar o `.csv` arquivo com êxito.

<u>Resultado real</u>:

A seguinte mensagem de erro é exibida: *&quot;A Chave de URL XYZ já foi gerada para um item com o SKU %sku%&quot;*, não é possível importar o arquivo.

## Correção

O patch está anexado a este artigo. Para baixá-lo, role para baixo até o final do artigo e clique no nome do arquivo ou clique no link a seguir:

[Baixar MDVA-12899\_EE\_2.2.3\_COMPOSER\_v2.patch](assets/MDVA-12899_EE_2.2.3_COMPOSER_v2.patch.zip)

### Versões compatíveis do Adobe Commerce:

A correção foi criada para:

* Adobe Commerce no local 2.2.3

O patch também é compatível (mas pode não resolver o problema) com as seguintes edições e versões do Adobe Commerce:

* Adobe Commerce na infraestrutura em nuvem de 2.2.0 para 2.2.7 e 2.3.0
* Adobe Commerce no local, de 2.2.0 para 2.2.2, de 2.2.4 para 2.2.7 e 2.3.0

## Como aplicar o patch

Consulte [Como aplicar um patch de compositor fornecido pelo Adobe Commerce](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) na nossa base de conhecimento de suporte para obter instruções.

## Links úteis

[Aplicar patches personalizados ao Adobe Commerce na infraestrutura em nuvem](https://devdocs.magento.com/guides/v2.3/cloud/project/project-patch.html)

## Arquivos Anexados
