---
title: "Adobe Commerce 2.4.2 B2B: o modelo de email não atualiza o email"
description: Este artigo descreve um problema B2B conhecido do Adobe Commerce 2.4.2 em que a atualização de algumas informações em um modelo de email não é atualizada nos emails. Esse problema afeta o conteúdo do email, como informações do cliente, taxas de moeda, símbolo da moeda, alteração de modelo de email etc. Não há uma solução disponível no momento, mas há uma solução alternativa na parte inferior deste artigo.
exl-id: 31b7086f-a941-4682-aa07-301ac31d543b
feature: B2B, Communications
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '278'
ht-degree: 0%

---

# Adobe Commerce 2.4.2 B2B: o modelo de email não atualiza o email

Este artigo descreve um problema B2B conhecido do Adobe Commerce 2.4.2 em que a atualização de algumas informações em um modelo de email não é atualizada nos emails. Esse problema afeta o conteúdo do email, como informações do cliente, taxas de moeda, símbolo da moeda, alteração de modelo de email etc. Não há uma solução disponível no momento, mas há uma solução alternativa na parte inferior deste artigo.

## Produtos e versões afetados

* Adobe Commerce no local 2.4.2
* Infraestrutura em nuvem do Adobe Commerce 2.4.2
* B2B 1.3.1

## Problema

<u>Etapas a serem reproduzidas</u>:

1. O Administrador da empresa cria uma OC (Ordem de compra) no front-end.
1. Verifique o email Aprovado automaticamente. A variável **nome do cliente** / **taxa de câmbio** devem ser valores esperados.
1. Alterar símbolo da moeda (**Lojas > Configuração > Configuração de Moeda > Opções de Moeda**) em Admin e nome do administrador da empresa na página Conta do cliente.
1. O Administrador do cliente cria outra OC no Administrador.
1. Verifique o email Aprovado automaticamente.

<u>Resultados esperados:</u>

O nome do cliente e o símbolo da moeda são alterados nos emails e têm seus novos valores conforme esperado.

<u>Resultados reais</u>:

O nome do cliente e o símbolo da moeda não são alterados nos emails e têm seus valores anteriores.

## Solução alternativa

Execute manualmente o job cron ou o consumidor para propagar as novas informações.

## Leitura relacionada

* [Gerenciar filas de mensagens](https://devdocs.magento.com/guides/v2.4/config-guide/mq/manage-message-queues.html) na documentação do desenvolvedor.
