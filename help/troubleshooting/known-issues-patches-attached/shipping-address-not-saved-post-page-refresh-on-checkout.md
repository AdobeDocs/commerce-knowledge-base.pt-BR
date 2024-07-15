---
title: Endereço de entrega não salvo pós-atualização da página no check-out
description: Este artigo fornece um patch para o problema conhecido do Adobe Commerce 2.2.3 em que o formulário de endereço de envio já preenchido do cliente estava em branco novamente após atualizar a página do navegador na finalização da compra do convidado. O problema ocorria quando o carrinho de compras persistente era ativado.
exl-id: b757e4af-7b1a-41bc-8460-9a6858c7aa5e
feature: Checkout, Orders, Shipping/Delivery
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# Endereço de entrega não salvo pós-atualização da página no check-out

Este artigo fornece um patch para o problema conhecido do Adobe Commerce 2.2.3 em que o formulário de endereço de envio já preenchido do cliente estava em branco novamente após atualizar a página do navegador na finalização da compra do convidado. O problema ocorria quando o carrinho de compras persistente era ativado.

## Problema

Os clientes passam pelo checkout do convidado e preenchem todos os formulários, inclusive o endereço de envio. Eles chegam à seção Revisar e pagamentos e recarregam a página. O formulário está vazio e eles precisam inserir novamente o endereço de entrega. A funcionalidade de carrinho de compras persistente está habilitada.

<u>Etapas a serem reproduzidas</u>:

**Pré-requisitos**: a funcionalidade de carrinho de compras persistente está habilitada. Verifique se está habilitado no Administrador, em **Lojas** > **Configuração** > **Clientes** ou **Lojas** > **Configuração** > **Vendas**, dependendo da sua versão do Adobe Commerce.

1. Vá para a loja.
1. Adicione produtos ao carrinho de compras.
1. Prossiga para o check-out como convidado.
1. Preencha o endereço de entrega, escolha as opções de envio e continue a garantir o pagamento.
1. Seja redirecionado para a seção Revisar e pagamentos do check-out.
1. Verifique novamente se o endereço de entrega é exibido na seção Enviar para.
1. Atualize a página.

<u>Resultado esperado</u>:

Você pode continuar o check-out e todos os dados serão salvos.

<u>Resultado real</u>:

O endereço de entrega está vazio, você precisa reinseri-lo.

## Correção

O patch está anexado a este artigo. Para baixá-lo, role para baixo até o final do artigo e clique no nome do arquivo ou clique no link a seguir:

[Baixar MDVA-9718\_EE\_2.2.3\_COMPOSER\_v1.patch](assets/MDVA-9718_EE_2.2.3_COMPOSER_v1.patch.zip)

### Versões compatíveis do Adobe Commerce

**O patch foi criado para:**

* Adobe Commerce 2.2.3

**O patch também é compatível (mas pode não resolver o problema) com as seguintes versões e edições do Adobe Commerce:**

* Adobe Commerce na infraestrutura em nuvem 2.1.13 - 2.1.18
* Adobe Commerce na infraestrutura em nuvem 2.2.0 - 2.2.5
* Adobe Commerce no local 2.0.X
* Adobe Commerce no local 2.1.X
* Adobe Commerce no local 2.2.0 - 2.2.2 e 2.2.4 - 2.2.5

## Como aplicar o patch

Para obter instruções, consulte [Como aplicar um patch de compositor fornecido pelo Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) em nossa base de dados de conhecimento de suporte.

## Arquivos Anexados
