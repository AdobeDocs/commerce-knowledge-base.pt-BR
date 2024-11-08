---
title: Erro de tempo limite de gateway 504 ao salvar uma categoria com mais de 1k produtos
description: Este artigo sugere uma solução para o problema de tempo limite que você pode ter ao executar operações com grandes categorias (mais de 1k produtos).
exl-id: 1f4b0385-215d-4d3d-8704-986c090824aa
feature: Cache, Categories, Marketing Tools, Products
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 0%

---

# Erro de tempo limite de gateway 504 ao salvar uma categoria com mais de 1k produtos

Este artigo sugere uma solução para o problema de tempo limite que você pode ter ao executar operações com grandes categorias (mais de 1k produtos).

## Produtos e versões afetados:

* Adobe Commerce na infraestrutura em nuvem 2.3.3
* Adobe Commerce no local 2.3.3
* Magento Open Source 2.3.3

## Problema

Pré-requisitos: A opção **Lojas** > **Configuração** > **CATÁLOGO** > **Catálogo** > **Usar Caminho de Categorias para URLs de Produtos** está definida como *Sim* para sua exibição de loja.

<u>Etapas a serem reproduzidas</u>

1. No Administrador do Commerce, vá para **Catálogo** > **Categorias**.
1. Abra uma categoria grande, como mais de 1000 produtos atribuídos.
1. Adicione um produto à categoria.
1. Clique em **Salvar categoria**.

<u>Resultado esperado:</u>

A categoria foi salva com sucesso.

<u>Resultado real:</u>

Após cinco minutos do processo de salvamento, a página de erro 504 gateway timeout é exibida.

## Causa

O processo demora mais do que o tempo limite configurado pelo servidor.

## Solução

Desabilitar a opção **Gerar substituições de URL de &quot;categoria/produto&quot;** removerá do banco de dados todas as substituições de URL de categoria/produto e diminuirá significativamente o tempo necessário para as operações com categorias grandes.

>[!WARNING]
>
>Desativar essa opção resultará na remoção permanente de substituições de URL de categoria/produto sem a capacidade de restaurá-las.

Para desabilitar a opção **Gerar regravações de URL de &quot;categoria/produto&quot;**:

1. No Administrador do Commerce, navegue até **Lojas** > **Configuração** > **CATÁLOGO** > **Catálogo**.
1. No canto superior esquerdo da página de configuração, no campo **Escopo**, defina o escopo de configuração como *Configuração Padrão*.
1. Definir **Gerar regravações de URL de &quot;categoria/produto&quot;** para *Não*.
1. Clique em **Salvar configuração**.
1. Limpar cache executando    ```bash    bin/magento cache:clean    ```    ou no Administrador do Commerce em **Sistema** > **Ferramentas** > **Gerenciamento de Cache**.

Agora é possível continuar a adicionar produtos às categorias ou mover categorias com um grande número de produtos, e essas operações levarão muito menos tempo e não devem causar tempo limite.

## Leitura relacionada

[Redirecionamentos Automáticos de Produto](https://experienceleague.adobe.com/en/docs/commerce-admin/marketing/seo/url-rewrites/url-redirect-product-automatic) em nosso guia do usuário.
