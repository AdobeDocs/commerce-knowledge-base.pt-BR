---
title: O check-out fica paralisado quando o método de pagamento Authorize.net é usado
description: Este artigo fornece uma explicação e uma correção para o problema do Adobe Commerce 2.3.X em que a finalização fica paralisada se Authorize.net for usado, com a mensagem de erro *'Não é possível ler a propriedade 'length' de null'* no log do console do navegador.
exl-id: 01dc1147-4010-4dc5-81f3-3b3015a8c47c
feature: Cache, Checkout, Console, Orders, Payments
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 8cd50456-5eb0-5364-922a-f14161feb828
    internal-label: Checkout
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 3dcbfa9e-51f8-569c-a0e4-7f59098f730f
    internal-label: Payments
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
  - id: c4af0798-d497-5e6b-8380-19812c26d00a
    internal-label: Console
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 0%
---
# O check-out fica paralisado quando o método de pagamento Authorize.net é usado

Este artigo fornece uma explicação e uma correção para o problema do Adobe Commerce 2.3.X em que o check-out fica interrompido se Authorize.net for usado, com a mensagem de erro *&#39;Não é possível ler a propriedade &#39;length&#39; de null&#39;* no log de console do navegador.

## Produtos e versões afetados

* Adobe Commerce 2.3.X

>[!NOTE]
>
>A integração de pagamento principal do Adobe Commerce Authorize.Net foi descontinuada desde a versão 2.3.4 e foi completamente removida na versão 2.4.0. Em vez disso, use uma extensão que atenda às suas necessidades da [Adobe Commerce [!DNL Marketplace]](https://commercemarketplace.adobe.com/).

## Problema

<u>Etapas a serem reproduzidas</u>

1. Configure o método de pagamento Authorize.net no Commerce Admin.
1. Vá para a loja.
1. Adicione um produto ao carrinho e prossiga para a finalização da compra.
1. Escolha Authorize.net como um método de pagamento.
1. Clique em **Fazer pedido**.

<u>Resultado esperado</u>

O iframe Authorize.net é carregado.

<u>Resultado real</u>

O ponteiro do Ajax é exibido e a página nunca é carregada. O seguinte erro JS é exibido no log do console do navegador: *&#39;TypeError Não Capturado: Não é possível ler a propriedade &#39;length&#39; de nulo em b (jstest.authorize.net/v1/AcceptCore.js:1)&#39;*

## Causa

Um dos motivos mais comuns para esse problema é a chave pública do cliente não ser especificada na configuração Authorize.Net no Commerce Admin.

## Solução

Em **Lojas** > **Configurações** > **Configuração** > **Vendas** > **Métodos de Pagamento**, na seção **Authorize.net**, verifique se o valor está especificado no campo **Chave Pública do Cliente**. Se estiver vazio, insira o valor da chave da sua conta de comerciante Authorize.Net.

Para que as alterações sejam aplicadas, limpe o cache executando

```bash
bin/magento cache:clean
```
