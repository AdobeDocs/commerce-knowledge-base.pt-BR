---
title: '"Erro 500" depois de clicar duas vezes em Remover link no carrinho de compras'''
description: Este artigo fornece um patch para o problema conhecido do Adobe Commerce na infraestrutura na nuvem 2.2.0 relacionado ao erro dos clientes ao tentar remover duas vezes um item do carrinho de compras (clicando duas vezes no link *Remover* ou clicando nele em guias diferentes).
exl-id: 927cf681-febf-42cc-8db5-469bcf8f2012
feature: Orders, Shopping Cart
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---

# &quot;Erro 500&quot; depois de clicar duas vezes em Remover link no carrinho de compras

Este artigo fornece um patch para o problema conhecido do Adobe Commerce na infraestrutura na nuvem 2.2.0 relacionado ao erro dos clientes ao tentar remover duas vezes um item do carrinho de compras (clicando duas vezes no link *Remover* ou clicando nele em guias diferentes).

## Problema

Quando os clientes clicam duas vezes no link *Remover* no carrinho de compras, tentando remover um produto do carrinho, eles recebem uma página em branco com a seguinte mensagem de erro: *&quot;Esta página não está funcionando. ERRO HTTP 500&quot;.* O mesmo problema acontece se um cliente abrir duas guias do navegador com a página do carrinho de compras e remover o produto primeiro em uma guia e depois na segunda.

<u>Etapas a serem reproduzidas</u>:

1. Adicione um produto ao carrinho de compras na loja.
1. Navegue até a página do carrinho de compras.
1. Clique duas vezes no link Remover.

OU

1. Adicione um produto ao carrinho de compras na loja.
1. Navegue até a página do carrinho de compras.
1. Abra uma nova guia do navegador e navegue até a página do carrinho de compras (mesmo produto).
1. Remova o produto do carrinho.
1. Abra a segunda guia e remova o produto novamente.

<u>Resultado esperado</u>: o produto foi removido do carrinho sem erros.

<u>Resultado real</u>: o produto foi removido com o erro: *&quot;Esta página não está funcionando. HTTP ERROR 500&quot;* mensagem de erro.

## Correção

O patch está anexado a este artigo. Para baixá-lo, role para baixo até o final do artigo e clique no nome do arquivo ou clique no link a seguir:

[Baixar MDVA-8623\_EE\_2.2.0\_v1.composer.patch](assets/MDVA-8623_EE_2.2.0_v1.composer.patch.zip)

## Versões compatíveis do Adobe Commerce:

A correção foi criada para:

* Adobe Commerce na infraestrutura em nuvem 2.2.0

O patch também é compatível (mas pode não resolver o problema) com as seguintes versões e edições do Adobe Commerce:

* Adobe Commerce na infraestrutura em nuvem 2.2.1 - 2.2.5
* Adobe Commerce no local 2.2.0 - 2.2.5

## Como aplicar o patch

Para obter instruções, consulte [Como aplicar um patch de compositor fornecido pelo Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) em nossa base de dados de conhecimento de suporte.

## Arquivos Anexados
