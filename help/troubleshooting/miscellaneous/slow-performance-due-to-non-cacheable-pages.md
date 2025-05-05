---
title: Desempenho lento devido a páginas não armazenáveis em cache
description: Este artigo fornece soluções para aumentar os tempos de carregamento do site ou as interrupções devido ao cache de página inteira (por exemplo, o Fastly) ter sido desativado para qualquer bloco em qualquer página que precise ser armazenada em cache.
exl-id: 7401d9bd-710c-4221-9c3d-d78042c1c1ad
feature: Cache, Categories
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---

# Desempenho lento devido a páginas não armazenáveis em cache

Este artigo fornece soluções para aumentar os tempos de carregamento do site ou as interrupções devido ao cache de página inteira (por exemplo, o Fastly) ter sido desativado para qualquer bloco em qualquer página que precise ser armazenada em cache.

## Produtos e versões afetados

* Adobe Commerce na infraestrutura em nuvem 2.x.x
* Adobe Commerce no local 2.x.x

### Problema

O site apresenta desempenho lento porque há blocos de cache em páginas que precisam ser armazenáveis em cache, mas foram definidas como `cacheable="false"`.

### Causa

Há páginas que precisam ser armazenadas em cache pelo Adobe Commerce. Essas páginas têm a maior taxa de transferência. Cada solicitação desses tipos de páginas, não do cache, torna o Adobe Commerce mais lento.

Essas páginas são:

* Categoria de catálogo (PLP)
* Página de detalhes do produto (PDP)
* Páginas de conteúdo estático (Página inicial, Fale conosco etc.)

Armazenável em cache e não armazenável em cache são termos usados para indicar se uma página deve ou não ser armazenada em cache. Por padrão, todas as páginas podem ser armazenadas em cache. No entanto, se qualquer bloco em um layout for designado como não armazenável em cache, a página inteira será armazenável em cache.

A captura de tela abaixo mostra um bloco com uma configuração `cacheable="false"` **&#x200B; ** que cria uma página não armazenável em cache.

![non_cacheable_kb.png](assets/non_cacheable_kb.png)

Os exemplos de páginas não armazenáveis em cache incluem páginas de comparação de produtos, carrinho e check-out.

A seguinte lista de páginas não é armazenada em cache (os caches Fastly, Block e Layout são evitados.). Isso ocorre devido à configuração &quot;armazenável em cache&quot; no layout.

### Solução

Verifique se os arquivos especificados acima têm a configuração `cacheable="false"`. Se eles tiverem ativado, verifique se essa configuração é necessária ou obrigatória.

* Se necessário, considere mover blocos não armazenáveis em cache para [mecanismo de conteúdo privado](https://developer.adobe.com/commerce/php/development/cache/page/private-content/).
* Se não for necessário, remova o atributo `cacheable="false"` e limpe o cache de layout.

>[!NOTE]
>
>Para o Adobe Commerce na infraestrutura em nuvem 2.4.1 e posterior, você pode usar a [Ferramenta de Análise do Site](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/site-wide-analysis-tool/access) para verificar automaticamente se o Cache de Página Inteira não está configurado corretamente.

### Leitura relacionada

[visão geral do cache do Adobe Commerce](https://developer.adobe.com/commerce/frontend-core/guide/caching/) na documentação do desenvolvedor.
