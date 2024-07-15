---
title: Problema de carrinho de compras vazio ao clicar várias vezes no check-out do minicarrinho
description: Este artigo fornece um patch para um problema conhecido do Adobe Commerce 2.2.3 relacionado ao fato de um carrinho de compras estar vazio depois que os clientes clicam em **Ir para check-out** várias vezes no minicarrinho de compras.
exl-id: 06b82c91-8998-4e7b-9fc0-671c9b2a2d3f
feature: Checkout, Orders, Shopping Cart
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 0%

---

# Problema de carrinho de compras vazio ao clicar várias vezes no check-out do minicarrinho

Este artigo fornece uma correção para um problema conhecido do Adobe Commerce 2.2.3 relacionado ao fato de um carrinho de compras estar vazio depois que os clientes clicam em **Ir para a finalização** várias vezes no minicarrinho de compras.

## Problema

Os clientes adicionam produtos ao carrinho e tentam fazer o check-out clicando no botão **Ir para o Check-out** várias vezes, mas quando eles vão para o carrinho, o carrinho fica vazio. O minicarrinho ainda pode mostrar produtos.

<u>Etapas a serem reproduzidas</u>:

1. Abra uma página de produto na loja.
1. Adicionar produtos ao carrinho.
1. No minicarrinho de compras, clique em **Ir para Check-out** várias vezes.

<u>Resultado esperado</u>:

O carrinho contém todos os produtos adicionados.

<u>Resultado real</u>:

Você não tem itens em seu carrinho de compras.

## Correção

Os patches estão anexados a este artigo. Para baixar um patch, role até o final do artigo e clique no nome de arquivo necessário ou clique em um dos links a seguir:

[Baixar MDVA-10441\_EE\_2.2.3\_v3.composer.patch](assets/MDVA-10441_EE_2.2.3_v3.composer.patch.zip)

[Baixar MDVA-17078\_EE\_2.2.5\_COMPOSER\_v1.patch](assets/MDVA-17078_EE_2.2.5_COMPOSER_v1.patch.zip)

### Versões compatíveis do Adobe Commerce

Os patches foram criados para:

* Adobe Commerce no local 2.2.3 (o arquivo `MDVA-10441_EE_2.2.3_v3.composer.patch`)
* Adobe Commerce na infraestrutura em nuvem 2.2.5 (arquivo `MDVA-17078_EE_2.2.5_COMPOSER_v1.patch`)

O patch `MDVA-10441_EE_2.2.3_v3.composer.patch` também é compatível (mas pode não resolver o problema) com as seguintes versões e edições do Adobe Commerce:

* Adobe Commerce nas versões 2.2.1 a 2.2.5 da infraestrutura em nuvem
* Versões locais do Adobe Commerce de 2.2.1 para 2.2.5

O patch `MDVA-17078_EE_2.2.5_COMPOSER_v1.patch` também é compatível (mas pode não resolver o problema) com as seguintes versões e edições do Adobe Commerce:

* Adobe Commerce 2.2.5

## Como aplicar um patch

Para obter instruções, consulte [Como aplicar um patch de compositor fornecido pelo Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) em nossa base de dados de conhecimento de suporte.

## Arquivos Anexados
