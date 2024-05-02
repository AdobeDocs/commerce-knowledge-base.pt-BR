---
title: O check-out fica paralisado quando o método de pagamento Authorize.net é usado
description: Este artigo fornece uma explicação e uma correção para o problema do Adobe Commerce 2.3.X em que a finalização fica paralisada se Authorize.net for usado, com a mensagem de erro *'Não é possível ler a propriedade 'length' de null'* no log do console do navegador.
exl-id: 01dc1147-4010-4dc5-81f3-3b3015a8c47c
feature: Cache, Checkout, Console, Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 0%

---

# O check-out fica paralisado quando o método de pagamento Authorize.net é usado

Este artigo fornece uma explicação e correção para o problema do Adobe Commerce 2.3.X em que a finalização fica paralisada se Authorize.net for usado, com a *&#39;Não é possível ler a propriedade &#39;length&#39; de null&#39;* mensagem de erro no log do console do navegador.

## Produtos e versões afetados

* Adobe Commerce 2.3.X

>[!NOTE]
>
>A integração de pagamento principal do Adobe Commerce Authorize.Net foi descontinuada desde a versão 2.3.4 e foi completamente removida na versão 2.4.0. Use uma extensão que atenda às suas necessidades no [Adobe Commerce [!DNL Marketplace]](https://commercemarketplace.adobe.com/) em vez disso.

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

O ponteiro do Ajax é exibido e a página nunca é carregada. O seguinte erro JS é exibido no log do console do navegador: *&#39;TypeError não capturado: não é possível ler a propriedade &#39;length&#39; de nulo em b (jstest.authorize.net/v1/AcceptCore.js:1)&#39;*

## Causa

Um dos motivos mais comuns para esse problema é a chave pública do cliente não ser especificada na configuração Authorize.Net no Commerce Admin.

## Solução

Em **Lojas** > **Configurações** > **Configuração** > **Vendas** > **Métodos de pagamento**, no **Authorize.net** verifique se o valor está especificado na variável **Chave pública do cliente** campo. Se estiver vazio, insira o valor da chave da sua conta de comerciante Authorize.Net.

Para que as alterações sejam aplicadas, limpe o cache executando

```bash
bin/magento cache:clean
```
