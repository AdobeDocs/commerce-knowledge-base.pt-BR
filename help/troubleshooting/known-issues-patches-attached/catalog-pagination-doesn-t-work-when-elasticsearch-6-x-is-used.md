---
title: A paginação de catálogo não funciona com o Elasticsearch 6.x
description: Este artigo fornece um patch para o problema do Adobe Commerce em que a paginação de catálogo não funciona no Elasticsearch 6.x.
exl-id: 60a423de-cf3a-4d73-a7cf-b6d9e95042ca
feature: Catalog Management, Categories, Search, Services
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---

# A paginação de catálogo não funciona com o Elasticsearch 6.x

Este artigo fornece um patch para o problema do Adobe Commerce em que a paginação de catálogo não funciona no Elasticsearch 6.x.

O patch abaixo soluciona problemas que os usuários do Adobe Commerce 2.3.3 experimentam em implantações em que o Elasticsearch 6.x é usado como mecanismo de pesquisa de catálogo. Os usuários veem uma mensagem de erro ao tentar navegar além da primeira página dos resultados da pesquisa.

Após a instalação deste patch, os usuários poderão percorrer todos os resultados da pesquisa.

## Produtos e versões afetados

* Adobe Commerce na infraestrutura em nuvem 2.3.3
* Adobe Commerce no local 2.3.3
* Magento Open Source 2.3.3
* Elasticsearch 6.x

## Problema

Foi descoberto um problema no Magento Open Source, no Adobe Commerce local e na infraestrutura do Adobe Commerce na nuvem, em que a paginação da página de resultados da pesquisa não funciona se você alternar a página.

<u>Etapas a serem reproduzidas</u>:

1. Instale o Adobe Commerce.
1. Ative o Elasticsearch 6 como um mecanismo de pesquisa de catálogo.
1. Adicione um número de produtos à Categoria que exceda o limite de uma página definido no Administrador. **Observação**: 12 é o número padrão de produtos exibidos por página no Adobe Commerce 2.3.3.
1. Abra Categoria na loja (resultados da pesquisa ou página de categoria) e vá para a página 2.

<u>Resultado esperado</u>:

Os produtos devem ser exibidos na segunda página.

<u>Resultado real</u>:

**&quot;***Não é possível encontrar produtos que correspondam à mensagem de seleção***&quot;** mostrada na segunda página.

## Solução

Para corrigir o problema, aplique a correção anexada a este artigo. Para baixá-lo, role para baixo até o final do artigo e clique no nome do arquivo ou clique no link a seguir:

[Problema de paginação do Catálogo de Downloads no patch do Elasticsearch 6.x](assets/Catalog_pagination_issue_on_Elasticsearch_6_composer-2019-10-11-08-07-41.patch.zip) - O patch é compatível com todas as versões e edições afetadas.

>[!WARNING]
>
>Adobe recomenda enfaticamente aplicar o patch o mais rápido possível, mesmo que você não tenha experimentado nenhum sintoma.

## Como aplicar o patch

Consulte [Como aplicar um patch de compositor fornecido pelo Adobe Commerce](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) para obter instruções.

## Arquivos anexados
