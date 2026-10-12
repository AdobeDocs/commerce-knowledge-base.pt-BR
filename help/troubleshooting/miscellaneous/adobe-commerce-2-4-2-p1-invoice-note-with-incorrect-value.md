---
title: 'Adobe Commerce 2.4.2-p1: nota de fatura com um valor incorreto'
description: Este artigo descreve um problema conhecido do Adobe Commerce 2.4.2-p1 em que uma nota fiscal com valor incorreto é gerada quando o grupo de clientes é alterado ao criar o pedido. Este problema foi corrigido na versão 2.4.3.
exl-id: bde90251-625f-4c9d-8e5a-9a2019656125
feature: Customer Service, Invoices
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 591c578b-908e-5b79-a9d3-931dfe60c24c
    internal-label: Invoices
  - id: da76473c-f99b-5ad0-9b14-896aed473f8a
    internal-label: Services
subfeature_v2:
  - id: deedbb4d-f1b7-58ea-a34a-de1f481f9d4c
    internal-label: Customer Service
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '229'
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

1. Crie uma **Conta de Cliente de Teste** e adicione-a ao **Grupo de Clientes de Varejo**.
1. Criar um **Novo Pedido** para o cliente de teste, adicionar **Produto** e **Endereço**.
1. Selecione **Método de envio**.
1. Na seção **Informações da Conta**, altere o grupo de clientes de **Retailer** para **Governo**.
1. Clique em **Fazer pedido**.
1. Clique em **Fatura** > **Enviar Fatura**.

<u>Resultados esperados</u>:

A seguinte observação deve aparecer na seção **Notas desta ordem**: &quot;Fatura de vértice enviada com êxito. Quantia: US$ 0,00.&quot;

<u>Resultados reais</u>:

A seguinte observação é exibida na seção **Observações para esta ordem**: &quot;Fatura Vertex enviada com êxito. Quantia: US$ 3,23.&quot;

## Solução

Este problema foi corrigido na versão 2.4.3.
