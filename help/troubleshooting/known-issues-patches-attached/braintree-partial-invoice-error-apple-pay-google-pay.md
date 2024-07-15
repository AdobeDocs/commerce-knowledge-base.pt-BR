---
title: "Adobe Commerce 2.4.4: não é possível criar faturas parciais"
description: Este artigo fornece uma correção para o problema em que os usuários não conseguem criar faturas parciais ao usar o Apple Pay ou o Google Pay through Braintree como métodos de pagamento.
exl-id: bf78cc07-9dc7-4eb8-bfdf-57ea5131effb
feature: Invoices, Orders, Payments
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 0%

---

# Adobe Commerce 2.4.4: Não é possível criar faturas parciais

Este artigo fornece uma correção para o problema em que os usuários não conseguem criar faturas parciais ao usar o Apple Pay ou o Google Pay through Braintree como métodos de pagamento.

## Produtos e versões afetados

Adobe Commerce (todos os métodos de implantação) 2.4.4

## Problema

Ao usar o Apple Pay ou o Google Pay como métodos de pagamento, os usuários obtêm o erro &quot;*O comando ‘vault_capture’ não existe. Verifique o comando e tente novamente.*&quot; ao criar faturas parciais.

<u>Etapas a serem reproduzidas</u>:

1. Abra o site do Adobe Commerce.
1. Adicione um produto simples ao carrinho (qtd. 2).
1. Escolha **Pagamento do Apple** ou **Pagamento do Google** como o método de pagamento do carrinho de compras.
1. Coloque o pedido.
1. Abrir detalhes do pedido no back-end.
1. Criar uma fatura parcial.
1. Criar outra fatura para o valor restante.

<u>Resultados esperados</u>:

As NFFs parciais são criadas.

<u>Resultados reais</u>:

A primeira NFF parcial é criada. Ao criar a segunda fatura parcial, os usuários recebem o seguinte erro: *O comando &#39;vault_capture&#39; não existe. Verifique o comando e tente novamente*.

## Causa

O Adobe Commerce salva os detalhes do cartão de crédito no cofre para criar NFFs parciais. Atualmente, não há nenhuma funcionalidade para o cofre do Apple Pay e do Google Pay.

## Solução

Para resolver o problema, aplique o seguinte patch:

[Braintree_disabled_partial_capture_for_applepay_googlepay.zip](assets/braintree-disabled-partial-capture-for-applepay-googlepay.zip)

## Como aplicar o patch

Consulte [Como aplicar um patch de compositor fornecido pelo Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) para obter instruções.
