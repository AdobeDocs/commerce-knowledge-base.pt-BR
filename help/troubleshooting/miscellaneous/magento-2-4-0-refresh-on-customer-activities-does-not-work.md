---
title: "Adobe Commerce 2.4.0: a atualização das Atividades do cliente não funciona"
description: Este artigo fornece uma solução para o problema conhecido do Adobe Commerce 2.4.0 quando um usuário administrador cria um pedido para um cliente e os botões de atualização no painel lateral Atividades do cliente não funcionam.
exl-id: 50048e9f-6009-4db5-ae4a-c35a84cec265
feature: Configuration
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# Adobe Commerce 2.4.0: a atualização das Atividades do cliente não funciona

Este artigo fornece uma solução para o problema conhecido do Adobe Commerce 2.4.0 quando um usuário administrador cria um pedido para um cliente e os botões de atualização no painel lateral Atividades do cliente não funcionam.

## Produtos e versões afetados

* Adobe Commerce no local 2.4.0
* Adobe Commerce na infraestrutura em nuvem 2.4.0

## Problema

<u>Etapas a serem reproduzidas</u>:

1. Vá para a **Painel de administração** > **Vendas** > **Pedidos**.
1. Clique em **Criar novo pedido** botão.
1. Selecione o cliente criado.
1. Acesse a loja como o cliente criado.
1. Vá para a **Produto** página. Clique em **Atualizar** botão no **Produtos visualizados recentemente** seção de **Atividades do cliente**.
1. Volte para a loja.
1. Fazer um pedido usando os produtos criados.
1. Volte para o **Painel de administração** e clique no link **Atualizar** botão do **Últimos itens solicitados** seção de **Atividades do cliente**.
1. Volte para a loja. Adicione o produto criado à **Lista de comparação**.
1. Volte para o **Painel de administração**. Clique em **Atualizar** botão do **Produtos na lista de comparação** seção de **Atividades do cliente**.
1. Volte para a loja.
1. Remova o produto criado da **Lista de comparação**.
1. Volte para o **Painel de administração**.
1. Clique em **Atualizar** botão do **Produtos comparados recentemente** seção de **Atividades do cliente**.
1. Volte para a loja.

<u>Resultados esperados</u>:

O nome do produto deve constar no campo **Produtos visualizados recentemente**, **Últimos itens solicitados**, **Produtos na lista de comparação**, e **Produtos comparados recentemente** seção.

<u>Resultados reais</u>:

A página é rolada para cima sempre que um **Atualizar** é clicado. O nome do produto não aparece na seção adequada.

## Solução

Uma solução alternativa é que o usuário administrador pode atualizar **Atividades do cliente** clicando no link **Atualizar alterações** na parte inferior da barra lateral. O problema está planejado para ser resolvido no patch do Adobe Commerce 2.4.1.

![mceclip0.png](assets/mceclip0.png)

## Leitura relacionada

* [Problema conhecido do Adobe Commerce 2.4.0: os métodos de pagamento de Braintree não são exibidos na finalização de vários endereços](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Problema conhecido na criação de etiquetas de remessa no Adobe Commerce 2.4.0](/help/troubleshooting/known-issues-patches-attached/shipping-labels-creation-known-issue-in-magento-2-4-0.md)
* [Problema conhecido do Adobe Commerce 2.4.0: exibição de dados de mensagens brutas na loja](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Problema conhecido do Adobe Commerce 2.4.0: as Taxas de imposto de exportação não funcionam](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Problema conhecido do Adobe Commerce 2.4.0: o botão &quot;Adicionar seleções ao carrinho&quot; não funciona](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
