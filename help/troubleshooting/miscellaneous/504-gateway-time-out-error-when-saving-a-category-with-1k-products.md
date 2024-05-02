---
title: Erro de tempo limite de gateway 504 ao salvar uma categoria com mais de 1k produtos
description: Este artigo sugere uma solução para o problema de tempo limite que você pode ter ao executar operações com grandes categorias (mais de 1k produtos).
exl-id: 1f4b0385-215d-4d3d-8704-986c090824aa
feature: Cache, Categories, Marketing Tools, Products
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
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

Pré-requisitos: o **Lojas** > **Configuração** > **CATÁLOGO** > **Catálogo** > **Usar caminho de categorias para URLs de produtos** está definida como *Sim* para a visualização da loja.

<u>Etapas a serem reproduzidas</u>

1. No Administrador do Commerce, acesse **Catálogo** > **Categorias**.
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

Desativar o **Gerar regravações de URL de &quot;categoria/produto&quot;** A opção removerá todas as substituições de URL de categoria/produto do banco de dados e reduzirá significativamente o tempo necessário para as operações com categorias grandes.

>[!WARNING]
>
>Desativar essa opção resultará na remoção permanente de substituições de URL de categoria/produto sem a capacidade de restaurá-las.

Para desativar o **Gerar regravações de URL de &quot;categoria/produto&quot;** opção:

1. No Administrador do Commerce, navegue até **Lojas** > **Configuração** > **CATÁLOGO** > **Catálogo**.
1. No canto superior esquerdo da página de configuração, na guia **Escopo** , defina seu escopo de configuração como *Configuração padrão*.
1. Definir **Gerar regravações de URL de &quot;categoria/produto&quot;** para *Não*.
1. Clique em **Salvar configuração**.
1. Limpar cache executando    ```bash    bin/magento cache:clean    ```    ou no Administrador do Commerce em **Sistema** > **Ferramentas** > **Gerenciamento de cache**.

Agora é possível continuar a adicionar produtos às categorias ou mover categorias com um grande número de produtos, e essas operações levarão muito menos tempo e não devem causar tempo limite.

## Leitura relacionada

[Redirecionamentos automáticos de produto](https://docs.magento.com/user-guide/v2.3/marketing/url-redirect-product-automatic.html) em nosso guia do usuário.
