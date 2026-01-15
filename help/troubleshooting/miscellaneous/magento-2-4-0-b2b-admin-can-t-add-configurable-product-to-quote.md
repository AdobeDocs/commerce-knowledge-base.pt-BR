---
title: O administrador B2B do Adobe Commerce 2.4.0 não pode adicionar o produto configurável à cotação
description: Este artigo fala sobre um problema conhecido no Administrador do Commerce ao gerenciar uma Cotação B2B. Não é possível adicionar um produto configurável por **SKU** à cotação. Ao clicar no botão **Adicionar à cotação**, a página de edição **Cotação** fica travada e você não pode configurar o produto e salvar as alterações. Esse problema também ocorre no Admin ao adicionar um produto por **SKU** a um pedido ou adicionar um produto por **SKU** na **Finalização avançada** (**Admin** &gt; **Clientes** &gt; **Todos os clientes** &gt; **Edição do cliente** &gt; **Gerenciar carrinho de compras**). Esse problema será resolvido em um patch para o Adobe Commerce 2.4.1.
exl-id: 73f7231b-b496-4250-b9e2-29427c772d56
feature: Admin Workspace, B2B, Catalog Management, Configuration, Products, Quotes
role: Developer
source-git-commit: 05297c82b292b8ccc88018c58e991bd3a32d6ffa
workflow-type: tm+mt
source-wordcount: '507'
ht-degree: 0%

---

# O administrador B2B do Adobe Commerce 2.4.0 não pode adicionar o produto configurável à cotação

Este artigo fala sobre um problema conhecido no Administrador do Commerce ao gerenciar uma Cotação B2B. Não é possível adicionar um produto configurável por **SKU** à cotação. Ao clicar no botão **Adicionar à Cotação**, a página de edição **Cotação** não é carregada e você não pode configurar o produto e salvar as alterações. Este problema também ocorre no Administrador ao adicionar um produto por **SKU** a um pedido ou adicionar um produto por **SKU** no **Check-out Avançado** (**Admin** > **Clientes** > **Todos os Clientes** > **Edição do Cliente** > **Gerenciar Carrinho de Compras**). Esse problema será resolvido em um patch para o Adobe Commerce 2.4.1.

## Produtos e versões afetados

* Adobe Commerce no local 2.4.0
* Adobe Commerce na infraestrutura em nuvem 2.4.0

## Problema

<u>Pré-condições</u>

* O Adobe Commerce 2.4.0 está instalado.
* B2B está instalado.
* Defina os recursos B2B como **Habilitar Empresa =** *Sim* , **Habilitar Catálogo Compartilhado =** *Não* e **Habilitar Cotação B2B =** *Sim*.
* Crie uma conta de cliente.
* Crie uma conta da empresa com o cliente criado anteriormente como o administrador da empresa.
* Crie um produto simples (Exemplo: nome &amp; **SKU** = TEST SIMPLE 1) que não esteja atribuído ao **Padrão (Geral)**.
* Faça com que o administrador da empresa solicite uma cotação usando o produto simples criado acima (Exemplo: TESTE SIMPLES 1).

<u>Etapas a serem reproduzidas</u>

1. Vá para o painel Administrador do Commerce.
1. Vá para **Vendas > Cotações**.
1. Abra a **Cotação**.
1. Clique no botão **Adicionar produto por SKU**.
1. Insira o **SKU** de outro produto (Exemplo: TEST SIMPLE 2) no campo de entrada **Inserir SKU**.
1. Insira alguma quantidade válida no campo de entrada **Qtd.**.
1. Clique no botão **Adicionar à Cotação**.

<u>Resultados esperados</u>

* A grade **Produtos Não Adicionados à Cotação**, contendo o nome e a **SKU** do produto criado, é exibida conforme esperado.
* Após a configuração do produto, o administrador poderá adicioná-lo à **Cotação** clicando no botão **Adicionar Produtos à Cotação**, conforme esperado.

<u>Resultados reais</u>

* A grade **Produtos Não Adicionados à Cotação**, contendo o nome e a **SKU** do produto criado, não é exibida.
* A página **Quote** está travando.

## Recomendação

Atualmente, não há solução alternativa para esse problema com a edição da Cotação B2B, mas para o gerenciamento de Pedidos e do Carrinho de Compras, é possível selecionar produtos da **Lista de Produtos** em vez de adicioná-los pela **SKU**. Um patch para resolver o problema estará disponível para o Adobe Commerce 2.4.1, cujo lançamento está programado para o quarto trimestre de 2020.

