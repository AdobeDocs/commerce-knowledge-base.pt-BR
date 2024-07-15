---
title: "Problema do Adobe Commerce 2.4.1: não é possível alterar a conta do Amazon no Chrome"
description: Este artigo descreve um problema conhecido do Adobe Commerce 2.4.1 em que os clientes entram nas contas do Amazon usadas anteriormente, em vez de serem sugeridos para fazer logon, ao usar o Amazon Pay durante a finalização da compra.
exl-id: 8acffe99-b3ec-4b45-9434-61b66e963838
feature: Customer Service
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# Problema do Adobe Commerce 2.4.1: não é possível alterar a conta do Amazon no Chrome

Este artigo descreve um problema conhecido do Adobe Commerce 2.4.1 em que os clientes entram nas contas do Amazon usadas anteriormente, em vez de serem sugeridos para fazer logon, ao usar o Amazon Pay durante a finalização da compra.

## Produtos e versões afetados

* Adobe Commerce no local 2.4.1
* Adobe Commerce na infraestrutura em nuvem 2.4.1

## Problema

Os clientes entram nas contas da Amazon usadas anteriormente, em vez de serem sugeridos a fazer logon ao usar o Amazon Pay durante o checkout.

<u>Etapas a serem reproduzidas:</u>

1. Na loja, adicione qualquer item ao carrinho de compras e prossiga para o check-out do convidado.
1. Clique no botão **Pagamento do Amazon**. Amazon.com sign in pop-up (pop-up de logon do) é exibido.
1. Faça logon na conta do Amazon.
1. Selecione um endereço e clique em **Avançar**.
1. Selecione o método de pagamento.
1. Clique em **Fazer pedido**.
1. Volte para a home page e faça logon na conta da loja.
1. Adicione qualquer item ao carrinho novamente e prossiga para o check-out.
1. Clique no botão **Pagamento do Amazon**.

<u>Resultado real:</u>

Você faz logon automaticamente na conta do Amazon usada anteriormente (Etapa 3) novamente.

<u>Resultado esperado:</u>

Amazon.com sign in pop-up é exibido e você pode fazer login ou criar uma nova conta para o Amazon Pay.

## Causa

O problema pode ocorrer em uma das seguintes situações:

* Quando o valor do cookie `SameSite` é `LAX`, o cookie não será enviado como parte de nenhuma chamada de terceiros.
* O recurso de bloqueio de conteúdo do Mozilla Firefox impede que terceiros rastreiem as atividades dos usuários do navegador, bloqueando o uso de scripts e mecanismos de armazenamento do lado do cliente. O Firefox usa um fornecedor externo, o Disconnect.me, para fornecer uma lista de sites de rastreamento a serem bloqueados. O Amazon Pay usa um iframe em um site de terceiros para retornar um token de acesso após o logon e renderizar o Endereço e o widget de carteira. Com o recurso de bloqueio de conteúdo, as solicitações de carregamento de iframe do Amazon Pay são consideradas solicitações de rastreamento de terceiros e são bloqueadas, resultando na impossibilidade de o comprador prosseguir com a finalização da compra.
* Qualquer situação em que cookies de terceiros ou JS estejam sendo explicitamente bloqueados pelo navegador.

## Solução

Verifique se as solicitações de iframe de Pagamento do Amazon não estão bloqueadas pelos navegadores.
