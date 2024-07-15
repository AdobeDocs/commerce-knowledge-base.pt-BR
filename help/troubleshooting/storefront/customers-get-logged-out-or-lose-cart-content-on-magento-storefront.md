---
title: Os clientes são desconectados ou perdem conteúdo do carrinho na loja da Adobe Commerce
description: Este artigo fornece uma solução e uma solução alternativa para o problema, em que os clientes são desconectados ou perdem itens do carrinho de compras na loja depois de serem redirecionados para a loja da Adobe Commerce a partir de pagamentos ou outros serviços de terceiros (o cookie de sessão é "perdido").
exl-id: 9175570c-b06c-4a65-b8ca-7a12ff266afb
feature: Orders, Page Content, Shopping Cart, Storefront
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '259'
ht-degree: 0%

---

# Os clientes são desconectados ou perdem conteúdo do carrinho na loja da Adobe Commerce

Este artigo fornece uma solução para o problema, em que os clientes são desconectados ou perdem itens do carrinho de compras na loja depois de serem redirecionados para a loja da Adobe Commerce a partir de pagamentos ou outros serviços de terceiros (o cookie de sessão é &quot;perdido&quot;).

## Produtos e versões afetados

* Adobe Commerce local, [todas as versões com suporte](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)
* Adobe Commerce na infraestrutura em nuvem, [todas as versões com suporte](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Problema

<u>Etapas a serem reproduzidas:</u>

1. O cliente adiciona produtos ao carrinho na loja e prossegue com o check-out.
1. O cliente é redirecionado para o site de terceiros para pagamento/envio ou outras informações/serviço.
1. O cliente é redirecionado de volta à loja.

<u>Resultado real:</u>

O cliente redirecionou para o carrinho de compras vazio ou para uma página em branco.

<u>Resultado esperado:</u>

O cliente redirecionou para uma página de pagamento bem-sucedido (ou outra página de sucesso), sem perder os dados de finalização e o progresso.

## Causa

O atributo de cookie SameSite está definido como *Lax* ou não foi especificado (que é tratado como definido como *Lax* ). Ter `SameSite` = *Lax* desabilita a transferência de um cookie para URLs externas por meio de solicitações `POST`.

## Solução

Para resolver o problema, entre em contato com o provedor de serviços de terceiros e solicite que seus desenvolvedores atualizem suas integrações para configurar parâmetros de cookie.

## Leitura relacionada

[Atualização do SameSite do Chrome](https://www.chromestatus.com/feature/5088147346030592)
