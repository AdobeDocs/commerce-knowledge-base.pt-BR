---
title: Pedidos não exibidos na grade Pedidos no Administrador
description: Este artigo fornece uma correção para o problema conhecido do Adobe Commerce 2.2.1 relacionado aos pedidos que não são exibidos na grade Pedidos no Administrador do Commerce.
exl-id: b8376760-6558-41ed-8c6b-51c5759e831a
feature: Admin Workspace, B2B, Cloud, Paas
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 0%

---

# Pedidos não exibidos na grade Pedidos no Administrador

Este artigo fornece uma correção para o problema conhecido do Adobe Commerce 2.2.1 relacionado aos pedidos que não são exibidos na grade Pedidos no Administrador do Commerce.

## Problema

No Adobe Commerce 2.2.1 com extensão B2B instalada, os pedidos criados na loja por um cliente registrado não são exibidos na lista de pedidos na conta do cliente no Administrador do Commerce. No log de depuração (`./var/log/debug.log`), o seguinte erro é registrado:

`report.CRITICAL: You cannot define a correlation name ‘company_order’ more than once`

<u>Pré-requisitos</u>:

O catálogo da loja contém produtos, não dados de amostra do Adobe Commerce, e a extensão B2B está instalada.

<u>Etapas a serem reproduzidas</u>:

1. Navegue até a loja e crie uma conta de cliente.
1. Adicione um produto ao carrinho, conclua o check-out e envie um pedido.
1. Faça logon no Administrador.
1. Navegue até **Clientes,** escolha **Todos os Clientes**.
1. Para o cliente recém-criado, clique em **Editar**.
1. Clique em **Pedidos** no painel à esquerda.

<u>Resultado esperado</u>:

O pedido enviado recentemente está listado na grade.

<u>Resultado real</u>:

A grade Pedidos não é exibida. Em vez disso, uma página em branco é exibida.

## Correção

O patch está anexado a este artigo. Para baixá-lo, role para baixo até o final do artigo e clique no nome do arquivo ou clique no link a seguir:

[Baixar MDVA-7868\_EE\_2.2.1\_v1\_composer.patch](assets/MDVA-7868_EE_2.2.1_v1_composer.patch.zip)

### Versões compatíveis do Adobe Commerce:

A correção foi criada para:

* Adobe Commerce no local 2.2.1

O patch também é compatível (mas pode não resolver o problema) com as seguintes versões e edições do Adobe Commerce:

* Adobe Commerce na infraestrutura em nuvem de 2.2.0 para 2.2.3
* Adobe Commerce no local 2.2.0 e 2.2.2 a 2.2.3

## Como aplicar o patch

Consulte [Como aplicar um patch de compositor fornecido pelo Adobe Commerce](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) na nossa base de conhecimento de suporte, para obter instruções.

## Arquivos Anexados
