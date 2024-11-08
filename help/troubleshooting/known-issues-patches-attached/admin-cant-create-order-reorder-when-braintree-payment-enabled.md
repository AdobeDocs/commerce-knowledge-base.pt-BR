---
title: O administrador não pode criar pedido/reordenação quando o pagamento Braintree está ativado
description: Este artigo fornece uma correção para o problema do Adobe Commerce 2.4.5 em que um usuário administrador não pode criar pedidos ou repedidos de clientes quando o método de pagamento Braintree está ativado.
exl-id: 8840aecb-21d9-4965-8c09-395e2d263aaa
feature: Admin Workspace, Native Luma Frontend Development, Orders, Payments
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 0%

---

# O administrador não pode criar pedido/reordenação quando o pagamento Braintree está ativado

Este artigo fornece uma correção para o problema do Adobe Commerce 2.4.5 em que um usuário administrador não pode criar pedidos ou repedidos de clientes quando o método de pagamento Braintree está ativado.

## Produtos e versões afetados

* Adobe Commerce na infraestrutura em nuvem 2.4.5
* Adobe Commerce no local 2.4.5
* Magento Open Source 2.4.5

## Problema

<u>Etapas a serem reproduzidas</u>:

1. A integração Braintree principal é usada (**Lojas** > **Configurações** > **Vendas** > **Método de Pagamento** > **Braintree**).
1. Usando a Loja Luma, faça um pedido.
1. Vá para Interface do Administrador > **Vendas**.
1. Tente criar um novo pedido para um cliente ou vá para um pedido feito anteriormente e clique em **Reordenar**.

<u>Resultado esperado</u>:

Os usuários administradores podem criar pedidos e repedidos com êxito para clientes quando o método de pagamento Braintree está habilitado.

<u>Resultado real</u>:

Os usuários administradores não podem criar pedidos nem reordenações para clientes quando o método de pagamento Braintree está habilitado e retorna o seguinte erro:

```bash
report.CRITICAL: Error: Call to a member function getMethodInstance() on null in /app/vendor/paypal/module-braintree-core/Block/Form.php:174
```

## Causa

Dependências de classe incorretas (`vendor/paypal/module-braintree-core/Block/Form.php`)

## Solução

Aplique o patch fornecido neste artigo.

## Correção

O patch está anexado a este artigo. Para baixá-lo, clique no link a seguir:

[BUNDLE-3137-composer.patch.zip](assets/BUNDLE-3137-composer.patch.zip)

>[!NOTE]
>
>Além disso, para o Adobe Commerce em comerciantes de infraestrutura em nuvem: o Adobe incluiu a correção nos Patches da nuvem para o Commerce versão 1.0.18. Consulte [Patches da nuvem para as notas de versão do Commerce](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/release-notes/cloud-patches) em nossa documentação do desenvolvedor para encontrar instruções sobre como aplicar o pacote mais recente.

### Versões compatíveis do Adobe Commerce:

A correção foi criada para:

* Adobe Commerce na infraestrutura em nuvem 2.4.5
* Adobe Commerce no local 2.4.5
* Magento Open Source 2.4.5

>[!NOTE]
>
>O patch não é compatível com nenhuma outra versão e edição do Adobe Commerce e Magento Open Source.

## Como aplicar o patch

Consulte [Como aplicar um patch de compositor fornecido pelo Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) em nossa base de dados de conhecimento de suporte para obter instruções.
