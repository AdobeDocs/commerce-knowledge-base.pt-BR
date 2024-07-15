---
title: Novos pedidos são enviados para arquivamento
description: Este artigo fornece um patch para o problema conhecido do Adobe Commerce 2.2.0 relacionado aos pedidos recém-criados exibidos no arquivo em vez da grade Pedidos no Administrador do Commerce.
exl-id: 37b70d28-0569-44f2-b677-29b2bde0bc5c
feature: Storage, Data Import/Export
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 0%

---

# Novos pedidos são enviados para arquivamento

Este artigo fornece um patch para o problema conhecido do Adobe Commerce 2.2.0 relacionado aos pedidos recém-criados exibidos no arquivo em vez da grade Pedidos no Administrador do Commerce.

>[!NOTE]
>
>O problema foi corrigido na versão 2.2.3 e posterior.

## Problema

Quando os clientes fazem pedidos, eles são exibidos na grade pedidos arquivados em vez da grade pedidos comuns.

<u>Etapas a serem reproduzidas</u>:

1. Adicione qualquer produto ao carrinho na loja, prossiga com o check-out e faça o pedido.
1. No Administrador do Commerce, navegue até **Vendas** > **Operações** > **Pedido**. Veja a ordem de exibição na grade.
1. Navegue até **Vendas** > **Arquivo** > **Pedidos**. Consulte a nova ordem na grade.

<u>Resultados esperados</u>:

A ordem é exibida somente na grade Pedidos.

<u>Resultados reais</u>:

A ordem é exibida na grade Pedidos e na grade de arquivamento de pedidos.

## Solução

Após a aplicação do patch, os pedidos serão exibidos na grade Pedido conforme esperado. Mas é necessário restaurar manualmente no Commerce Admin os que foram enviados para arquivamento antes da aplicação do patch.

## Correção

O patch está anexado a este artigo. Para baixá-lo, role para baixo até o final do artigo e clique no nome do arquivo ou clique no link a seguir:

[Baixar MDVA-8007\_EE\_2.2.0\_v1.composer.patch](assets/MDVA-8007_EE_2.2.0_v1.composer.patch.zip)

### Versões compatíveis do Adobe Commerce:

A correção foi criada para:

* Adobe Commerce 2.2.0

O patch também é compatível (mas pode não resolver o problema) com as seguintes versões e edições do Adobe Commerce:

* Adobe Commerce no local, Adobe Commerce na infraestrutura em nuvem 2.2.1 - 2.2.3

## Como aplicar o patch

Para obter instruções, consulte [Como aplicar um patch de compositor fornecido pelo Adobe Commerce](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) em nossa base de dados de conhecimento de suporte.

## Links úteis em nosso guia do usuário

* [Gerenciar ordens arquivadas](https://docs.magento.com/user-guide/sales/order-archive.html)

## Arquivos Anexados
