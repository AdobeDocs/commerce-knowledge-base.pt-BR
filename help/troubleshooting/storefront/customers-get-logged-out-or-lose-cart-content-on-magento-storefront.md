---
title: Os clientes são desconectados ou perdem conteúdo do carrinho na loja da Adobe Commerce
description: Este artigo fornece uma solução e uma solução alternativa para o problema, em que os clientes são desconectados ou perdem itens do carrinho de compras na loja depois de serem redirecionados para a loja da Adobe Commerce a partir de pagamentos ou outros serviços de terceiros (o cookie de sessão é "perdido").
exl-id: 9175570c-b06c-4a65-b8ca-7a12ff266afb
feature: Orders, Page Content, Shopping Cart, Storefront
role: Admin
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 17d326fa-534a-55a5-b46f-8ae1de1e2f75
    internal-label: Page Content
  - id: df8eaa0e-dd74-553a-8ad5-28129f8e8d3d
    internal-label: Shopping Cart
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
    internal-label: Storefront
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '285'
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
