---
title: A entrega direta coleta o endereço errado
description: A solução de envio não coleta o endereço de origem do produto.
exl-id: ce89713f-d506-4e4f-bf49-cdee3e6d29b5
feature: Customer Service, Orders, Shipping/Delivery
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '115'
ht-degree: 0%

---

# A entrega direta coleta o endereço errado

## Problema

A solução de envio não coleta o endereço de origem do produto.

## Produtos e versões afetados

* Adobe Commerce na infraestrutura em nuvem (todas as versões), com o Magento Inventory instalado
* Adobe Commerce no local 2.3.0 e posterior, com inventário de Magento instalado
* Magento Open Source 2.3.0 e mais recente, com inventário de Magento instalado

### Causa

No momento, o Inventário Magento não permite usar o cálculo de taxas de entrega direta com base no endereço de origem durante a finalização da compra. Em vez disso, o endereço de armazenamento padrão da configuração é usado em todos os casos.

## Leitura relacionada

* [Perguntas frequentes sobre o Inventário de Magento](https://github.com/magento/inventory/wiki/MSI-FAQs) no GitHub.
