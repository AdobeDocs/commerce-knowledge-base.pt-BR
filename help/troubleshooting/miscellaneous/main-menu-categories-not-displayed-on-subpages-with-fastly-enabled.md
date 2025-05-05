---
title: O menu principal (Categorias) não é exibido em subpáginas com o recurso Fastly ativado
description: Este artigo fornece uma correção para quando o Menu principal (ou o [menu de Navegação superior da categoria](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation-top.html?lang=pt-BR) em nosso guia do usuário) não é exibido na loja para subpáginas (por exemplo, *blog/página*) quando o Fastly ou o Varnish está ativado.
exl-id: 7c54791d-8aa6-4f01-a28b-a7aecdb8ff74
feature: Categories, Marketing Tools
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# O menu principal (Categorias) não é exibido em subpáginas com o recurso Fastly ativado

Este artigo fornece uma correção para quando o Menu principal (ou o [menu de Navegação superior da categoria](/docs/commerce-admin/catalog/catalog/navigation/navigation-top.html) do guia do usuário) não é exibido na loja para subpáginas (por exemplo, *blog/página*) quando o Fastly ou o Varnish está habilitado.

**Causa:** o caractere `/` não permitido (barra) no parâmetro *Chave de URL* da página (configurações de Otimização do Mecanismo de Pesquisa). O caractere geralmente é adicionado quando o *Caminho da URL* (com o local inteiro da página) é especificado por engano em vez da *Chave da URL*: por exemplo, *blog/página\_nome* em vez de apenas *página\_nome*.

**Solução:** remova o caractere `/` (barra); para o parâmetro *Chave de URL*, especifique apenas o nome da página.

## Versões afetadas

* Adobe Commerce no local 2.X.X
* Adobe Commerce na infraestrutura em nuvem 2.X.X
* Fastly ou Varnish

## Problema

O menu principal (também conhecido como [menu de navegação superior da categoria](/docs/commerce-admin/catalog/catalog/navigation/navigation-top.html) em nosso guia do usuário) não é exibido na loja para subpáginas quando o Fastly ou outros serviços baseados em Verniz são habilitados.

## Causa

O problema é causado pelo caractere `/` não permitido (barra), adicionado ao parâmetro *Chave de URL* (configurações de Otimização do Mecanismo de Pesquisa).

O caractere geralmente é adicionado quando o *Caminho da URL* (com o local inteiro da página, incluindo o recurso/diretório pai da página) é especificado por engano em vez da *Chave da URL*: por exemplo, *blog/página\_nome* em vez de apenas *página\_nome*.

![Parâmetro de Chave de URL para configurações de SEO](assets/seo_url_key.png)

## Solução

Remova o caractere `/` (barra) do parâmetro *Chave de URL* para todas as páginas do armazenamento.

Em outras palavras, use a *Chave de URL* em vez do *Caminho da URL*: mencione apenas o nome da página sem um recurso/diretório pai.

### Recommendations na hierarquia de páginas e SEO

Para definir a hierarquia de página, use a seção **Hierarquia** do menu Editar Página.

![Configurações de hierarquia](assets/hierarchy_hr.png)

Você também pode usar o menu **Conteúdo** > **Elementos** > **Hierarquia** - para soluções de hierarquia mais complexas.

Para fins de SEO em páginas de produtos, use Substituições de URL (**Marketing** > **SEO e Pesquisa** > **Substituições de URL**).

## Mais informações em nosso guia do usuário

O parâmetro *Chave de URL* para SEO:

* [Otimização do mecanismo de pesquisa](/docs/commerce-admin/catalog/categories/create/categories-search-engine-optimization.html)
* [Adicionar uma nova página](/docs/commerce-admin/content-design/elements/pages/page-add.html)

Hierarquia da página:

* [Visão geral](/docs/commerce-admin/content-design/elements/pages/page-hierarchy.html)
* [Adicionando um nó](/docs/commerce-admin/content-design/elements/pages/page-hierarchy.html#add-a-hierarchy-node)
