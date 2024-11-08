---
title: Os usuários não podem adicionar o produto ao carrinho se nada estiver selecionado em Permitir países
description: Este artigo fornece um patch para o Adobe Commerce 2.4.4 conhecido com o problema do PHP 8.1 em que os usuários não podem adicionar produtos ao carrinho se a opção Permitir países não estiver selecionada.
exl-id: d05d1956-de23-496c-9234-c461a3cfdf36
feature: Orders, Products, Shopping Cart
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '307'
ht-degree: 0%

---

# Os usuários não podem adicionar o produto ao carrinho se nada estiver selecionado em Permitir países

Este artigo fornece um patch para o Adobe Commerce 2.4.4 conhecido com o problema do PHP 8.1 em que os usuários não podem adicionar produtos ao carrinho se a opção Permitir países não estiver selecionada.

## Produtos e versões afetados

Adobe Commerce 2.4.4 com PHP 8.1

## Problema

Os usuários não poderão adicionar produtos ao carrinho se a opção Permitir países não estiver selecionada.

<u>Etapas a serem reproduzidas</u>:

1. Faça logon no Administrador do Commerce.
1. Ir para **Loja** > **Configuração** > **Geral** > **Opções de País**
1. Desmarque todas as opções no campo **Permitir países**.
1. Clique em **Salvar configuração** para salvar a configuração.
1. Acesse a loja e tente adicionar um produto ao carrinho.

<u>Resultado Esperado:</u>

Você pode adicionar um produto ao carrinho.

<u>Resultado Real:</u>

Não é possível adicionar um produto ao carrinho. Você recebe o seguinte erro de console:

```bash
Failed to load resource: the server responded with a status of 400 (Bad Request)
customer-data.js:87 Uncaught Error: [object Object]
    at Object.<anonymous> (customer-data.js:87:23)
    at fire (jquery.js:3500:50)
    at Object.fireWith [as rejectWith] (jquery.js:3630:29)
    at done (jquery.js:9798:30)
    at XMLHttpRequest.<anonymous> (jquery.js:10057:37)
```

## Causa

A configuração do Adobe Commerce recupera `null` caso uma configuração de multisseleção não tenha itens selecionados. Esta configuração se for processada com sucesso nas versões do PHP anteriores à 8.1. Entretanto, no PHP 8.1 ele não funciona corretamente devido aos erros que são causados pelo &quot;[Deprecate transmitindo null para argumentos não-nulos de funções internas no PHP 8.1](https://wiki.php.net/rfc/deprecate_null_to_scalar_internal_arg)&quot;.

## Soluções

Para resolver o problema, aplique o seguinte patch:

[AC-2655_2.4.4.patch.zip](assets/AC-2655_2.4.4.patch.zip)

## Como aplicar o patch

Consulte [Como aplicar um patch de compositor fornecido pelo Adobe Commerce](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) em nossa base de dados de conhecimento de suporte para obter instruções.

## Links úteis

[Aplique patches personalizados ao Adobe Commerce na infraestrutura na nuvem](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) na documentação do desenvolvedor.
