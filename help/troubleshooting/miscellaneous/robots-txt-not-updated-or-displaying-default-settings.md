---
title: robots.txt não atualizado ou exibindo configurações padrão
description: O artigo fornece uma solução para quando você configurar "robots.txt" corretamente, por exemplo, para [Práticas recomendadas para o Adobe Commerce robots.txt](https://support.magento.com/hc/en-us/articles/360048754931), mas o "robots.txt" não está sendo atualizado ou está exibindo as configurações padrão.
exl-id: 629b1247-9282-49f9-ada3-a804ddbaa0f5
feature: Configuration
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 0%

---

# robots.txt não atualizado ou exibindo configurações padrão

O artigo fornece uma solução para quando você configura o `robots.txt` corretamente, por exemplo, de acordo com as [Práticas recomendadas para o Adobe Commerce robots.txt](https://support.magento.com/hc/en-us/articles/360048754931), mas o `robots.txt` não está sendo atualizado ou está exibindo as configurações padrão.

## Produtos e versões afetados

* Adobe Commerce na infraestrutura em nuvem 2.3.x, 2.4.x

## Problema

Não é possível alterar a configuração padrão `robots.txt`.

<u>Etapas a serem reproduzidas:</u>

1. Acesse o painel Administração.
1. Adicione conteúdo a **Conteúdo** > Design > **Configuração** > **Editar instrução personalizada do arquivo`robots.txt`**, como o texto &quot;Olá&quot;, e salve as alterações.
1. Visite a URL `robots.txt`.

<u>Resultado esperado:</u>
`robots.txt` tem o texto salvo.

<u>Resultado real:</u>

O arquivo `robots.txt` não é alterado.

## Causa

A indexação por mecanismos de pesquisa está desativada.

## Solução

Habilitar indexação por mecanismos de pesquisa. Consulte [Configurar indexação por mecanismo de pesquisa](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure-store/robots-sitemap#configure-indexing-by-search-engine) na documentação do desenvolvedor.

## Leitura relacionada

* [Adicionar o mapa do site e os robôs do mecanismo de pesquisa](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure-store/robots-sitemap) à documentação do desenvolvedor.
