---
title: A consulta do GraphQL para ocultar categorias não funciona com o catálogo compartilhado B2B
description: Este artigo fornece uma solução para quando o recurso de catálogo compartilhado B2B não estiver funcionando com a consulta de categorias do GraphQL para ocultar categorias.
exl-id: bdafa8d9-b637-409e-86b5-d132bccfe0b8
feature: B2B, Catalog Management, Categories, GraphQL, Customer Service
role: Developer
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 0%

---

# A consulta do GraphQL para ocultar categorias não funciona com o catálogo compartilhado B2B


## Produtos e versões afetados

* Adobe Commerce na infraestrutura em nuvem e Adobe Commerce no local 2.4.3

## Problema

As categorias do GraphQL e as consultas `categoryList` ignoram a permissão de categoria para ocultar categorias em um catálogo compartilhado. Isso acontece com todos os comerciantes no Adobe Commerce 2.4.3 com o recurso Catálogo compartilhado B2B ativado.

<u>Etapas a serem reproduzidas</u>:

Pré-requisitos:

Isso acontece com todos os comerciantes no Adobe Commerce 2.4.3 com a loja de PWA consumindo a API do GraphQL com o back-end/administrador do Adobe Commerce tendo o recurso Catálogo compartilhado B2B ativado.

1. Crie várias categorias (CAT1, CAT2).
1. Criar um catálogo compartilhado privado.
1. Crie um usuário da empresa e atribua-o ao catálogo compartilhado acima.
1. Atribua alguns produtos a cada uma dessas categorias.
1. Atribua CAT1 ao catálogo personalizado, cancele a atribuição de CAT2 ao catálogo privado personalizado. Isso desatribui todos os produtos de CAT2 do catálogo compartilhado.
1. Salve o catálogo personalizado.
1. Defina a permissão de categoria para CAT2 como *Negar* categoria de navegação e defina o grupo de clientes para o catálogo privado acima.
1. Execute a consulta `categoryList query` ou categorias como o usuário da empresa a partir da etapa três.

<u>Resultados esperados</u>:

Somente o CAT1 é exibido nos resultados.

<u>Resultados reais</u>:

Todas as categorias são exibidas, independentemente de serem atribuídas/não atribuídas no catálogo compartilhado ou quais são as permissões da categoria.

## Causa

A funcionalidade não foi implementada.

## Solução

O problema será corrigido no escopo da versão 2.4.4, e os comerciantes devem [enviar um tíquete](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) para obter um patch personalizado se precisarem de uma solução antes da versão 2.4.4.

## Leitura relacionada

* [Limites de número de categorias do Adobe Commerce de práticas recomendadas](https://support.magento.com/hc/en-us/articles/360048176832) em nossa base de dados de conhecimento de suporte.
