---
title: O menu principal (Categorias) não é exibido em subpáginas com o recurso Fastly ativado
description: Este artigo fornece uma correção para quando o Menu principal (ou o [menu de Navegação superior da categoria](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation-top.html) em nosso guia do usuário) não é exibido na loja para subpáginas (por exemplo, *blog/página*) quando o Fastly ou o Varnish está ativado.
exl-id: 7c54791d-8aa6-4f01-a28b-a7aecdb8ff74
feature: Categories, Marketing Tools
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# O menu principal (Categorias) não é exibido em subpáginas com o recurso Fastly ativado

Este artigo fornece uma correção para quando o menu principal (ou a variável [Menu de Navegação Superior de Categoria](/docs/commerce-admin/catalog/catalog/navigation/navigation-top.html) no nosso guia do usuário) não é exibido na loja para subpáginas (por exemplo, *blog/página*) quando Fastly ou Varnish estiver ativado.

**Causa:** o não permitido `/` caractere na caixa *Chave do URL* parâmetro da página (definições de Otimização do Mecanismo de Pesquisa). O caractere geralmente é adicionado quando *Caminho do URL* (com o local inteiro da página) é especificado por engano em vez de *Chave do URL*: por exemplo, *blog/page\_name* em vez de apenas *page\_name*.

**Solução:** remover o `/` caractere (barra); para a variável *Chave do URL* parâmetro, especifique somente o nome da página.

## Versões afetadas

* Adobe Commerce no local 2.X.X
* Adobe Commerce na infraestrutura em nuvem 2.X.X
* Fastly ou Varnish

## Problema

O menu principal (também conhecido como [Menu de Navegação Superior de Categoria](/docs/commerce-admin/catalog/catalog/navigation/navigation-top.html) no nosso guia do usuário) não é exibido na loja para subpáginas quando o Fastly ou outros serviços baseados em Vernish estão habilitados.

## Causa

O problema é causado pela permissão `/` caractere (barra), adicionado à *Chave do URL* (Configurações de Otimização do Mecanismo de Pesquisa).

O caractere geralmente é adicionado quando *Caminho do URL* (com o local inteiro da página, incluindo o recurso/diretório principal da página) é especificado por engano, em vez de *Chave do URL*: por exemplo, *blog/page\_name* em vez de apenas *page\_name*.

![Parâmetro de Chave de URL para configurações de SEO](assets/seo_url_key.png)

## Solução

Remova o `/` caractere (barra) da *Chave do URL* parâmetro para todas as páginas da loja.

Em outras palavras, use *Chave do URL* em vez de *Caminho do URL*: mencione apenas o nome da página sem nenhum recurso/diretório principal.

### Recommendations na hierarquia de páginas e SEO

Para definir a hierarquia de página, use o **Hierarquia** seção do menu Editar página.

![Configurações de hierarquia](assets/hierarchy_hr.png)

Você também pode usar o **Conteúdo** > **Elementos** > **Hierarquia** menu - para obter soluções de hierarquia mais complexas.

Para fins de SEO em páginas de produtos, use substituições de URL (**Marketing** > **SEO e pesquisa** > **Substituições de URL**).

## Mais informações em nosso guia do usuário

A variável *Chave do URL* parâmetro para SEO:

* [Otimização do mecanismo de pesquisa](/docs/commerce-admin/catalog/categories/create/categories-search-engine-optimization.html)
* [Adicionar uma nova página](/docs/commerce-admin/content-design/elements/pages/page-add.html)

Hierarquia da página:

* [Visão geral](/docs/commerce-admin/content-design/elements/pages/page-hierarchy.html)
* [Adicionando um nó](/docs/commerce-admin/content-design/elements/pages/page-hierarchy.html#add-a-hierarchy-node)
