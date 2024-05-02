---
title: O laminas/laminas-escaper 2.7.1 causa erros no Adobe Commerce front-end e nas páginas de administração
description: Este artigo fornece uma solução para o problema em que o lançamento do laminas/laminas-escaper:2.7.1 quebra a funcionalidade do Adobe Commerce no gerenciamento de produtos, categorias e páginas de produtos. Este problema será corrigido no Adobe Commerce 2.4.3.
exl-id: 89de6827-7b90-4f08-92fb-56ed31ae2672
feature: Admin Workspace, Categories
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '198'
ht-degree: 0%

---

# O laminas/laminas-escaper 2.7.1 causa erros no Adobe Commerce front-end e nas páginas de administração


## Produtos e versões afetados

* Adobe Commerce na arquitetura 2.3.5+
* Adobe Commerce 2.3.5+

## Problema

Após a atualização para laminas/laminas-escaper:2.7.1, uma mensagem de erro é exibida na página.

<u>Etapas a serem reproduzidas</u>:

Atualizar laminas/laminas-escaper para 2.7.1.

<u>Resultado esperado</u>:

Nenhum erro.

<u>Resultado real</u>:

Após a atualização para laminas/laminas-escaper:2.7.1, uma mensagem de erro é exibida em uma página de edição de produto (ou gerenciamento de produto): *TypeError: rawurlencode() espera que o parâmetro 1 seja uma sequência de caracteres, int fornecido em /var/www/magento/vendor/laminas/laminas-escaper/src/Escaper.php:246*
Esse erro ocorre nas páginas de front-end e de Administração, causando distorção no conteúdo da página.

## Causa

o laminas/laminas-escaper 2.7.1 começou a usar validação de tipo estrita para a classe Escaper.

## Solução

Executar `composer require laminas/laminas-escaper:2.7.0` no diretório raiz de cada projeto.

## Leitura relacionada

laminas Documentação: [Lâminas de escape](https://docs.laminas.dev/laminas-escaper/)
