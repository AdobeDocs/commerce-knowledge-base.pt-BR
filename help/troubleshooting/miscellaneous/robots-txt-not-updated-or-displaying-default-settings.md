---
title: robots.txt não atualizado ou exibindo configurações padrão
description: O artigo fornece uma solução para quando você configurar "robots.txt" corretamente, por exemplo, para [Práticas recomendadas para o Adobe Commerce robots.txt](https://support.magento.com/hc/en-us/articles/360048754931), mas o "robots.txt" não está sendo atualizado ou está exibindo as configurações padrão.
exl-id: 629b1247-9282-49f9-ada3-a804ddbaa0f5
feature: Configuration
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 0%

---

# robots.txt não atualizado ou exibindo configurações padrão

O artigo fornece uma solução para quando você configurar `robots.txt` corretamente, por exemplo, por [Práticas recomendadas para o Adobe Commerce robots.txt](https://support.magento.com/hc/en-us/articles/360048754931) mas o `robots.txt` O não está sendo atualizado ou está exibindo as configurações padrão.

## Produtos e versões afetados

* Adobe Commerce na infraestrutura em nuvem 2.3.x, 2.4.x

## Problema

Não é possível alterar o padrão `robots.txt` configuração.

<u>Etapas a serem reproduzidas:</u>

1. Acesse o painel Administração.
1. Adicionar conteúdo a **Conteúdo** > Design > **Configuração** > **Editar instrução personalizada de`robots.txt`** como o texto &quot;olá&quot; e salve as alterações.
1. Visite o `robots.txt` url.

<u>Resultado esperado:</u>
`robots.txt` tem o texto salvo.

<u>Resultado real:</u>

`robots.txt` arquivo não é alterado.

## Causa

A indexação por mecanismos de pesquisa está desativada.

## Solução

Habilitar indexação por mecanismos de pesquisa. Consulte [Configurar indexação por mecanismo de pesquisa](https://devdocs.magento.com/cloud/trouble/robots-sitemap.html#configure-indexing-by-search-engine) na documentação do desenvolvedor.

## Leitura relacionada

* [Adicionar mapa do site e robôs de mecanismo de pesquisa](https://devdocs.magento.com/cloud/trouble/robots-sitemap.html) na documentação do desenvolvedor.
