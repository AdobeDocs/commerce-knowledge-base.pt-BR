---
title: "Adobe Commerce 2.4.2-p1: nota fiscal com um valor incorreto"
description: Este artigo descreve um problema conhecido do Adobe Commerce 2.4.2-p1 em que uma nota fiscal com valor incorreto é gerada quando o grupo de clientes é alterado ao criar o pedido. Este problema foi corrigido na versão 2.4.3.
exl-id: bde90251-625f-4c9d-8e5a-9a2019656125
feature: Customer Service, Invoices
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 0%

---

# Adobe Commerce 2.4.2-p1: nota de fatura com um valor incorreto

Este artigo descreve um problema conhecido do Adobe Commerce 2.4.2-p1 em que uma nota fiscal com valor incorreto é gerada quando o grupo de clientes é alterado ao criar o pedido. Este problema foi corrigido na versão 2.4.3.

## Produtos e versões afetados

* Adobe Commerce no local 2.4.2-p1
* Adobe Commerce na infraestrutura em nuvem 2.4.2-p1

## Problema

Quando o grupo de clientes é alterado no momento da criação da ordem, a fatura é gerada com uma nota de fatura incorreta.

<u>Etapas a serem reproduzidas</u>:

1. Criar um **Testar Conta do Cliente** e adicione-o à **Grupo de Clientes de Varejo**.
1. Criar um **Novo pedido** para o cliente de teste, adicione **Produto** e **Endereço**.
1. Selecionar **Método de envio**.
1. No **Informações da conta** seção, alterar grupo de clientes de **Varejista** para **Governo**.
1. Clique em **Fazer pedido**.
1. Clique em **Fatura** > **Enviar fatura**.

<u>Resultados esperados</u>:

A seguinte nota deve aparecer sob o título **Notas deste pedido**  seção: &quot;Fatura de vértice enviada com êxito. Quantia: US$ 0,00.&quot;

<u>Resultados reais</u>:

A seguinte observação aparece sob o **Notas deste pedido** seção: &quot;Fatura de vértice enviada com êxito. Quantia: US$ 3,23.&quot;

## Solução

Este problema foi corrigido na versão 2.4.3.
