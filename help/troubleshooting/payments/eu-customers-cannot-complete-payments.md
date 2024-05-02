---
title: Clientes da UE não podem concluir pagamentos
description: Este artigo fornece uma correção para o problema de clientes da União Europeia não poderem concluir os pagamentos.
exl-id: 8309d96b-47a3-4d27-b538-e6e3bcdfb7d4
feature: Orders, Payments
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '193'
ht-degree: 0%

---

# Clientes da UE não podem concluir pagamentos

Este artigo fornece uma correção para o problema de clientes da União Europeia não poderem concluir os pagamentos.

## Produtos e versões afetados

* Adobe Commerce na infraestrutura em nuvem, todas as versões
* Adobe Commerce no local 2.2.x, 2.3.x
* Magento Open Source 2.2.x, 2.3.x

## Problema

Os clientes da UE queixam-se de que as suas transações com cartões de crédito estão a ser recusadas.

## Causa

A União Europeia reviu um regulamento denominado Diretiva Serviços de Pagamento (PSD) com uma versão atualizada [PSD 2](https://eur-lex.europa.eu/legal-content/EN/TXT/HTML/?uri=CELEX:32015L2366&amp;from=EN). Trata-se de uma diretiva da União Europeia (UE) aplicada para regulamentar serviços de pagamento e prestadores de serviços de pagamento em toda a UE e no Espaço Econômico Europeu (EEE). A SCA (Autenticação de Cliente Forte) é um requisito do PSD2 para aumentar a segurança e a autenticação dos dados de pagamento. Se suas soluções de pagamento não cumprirem os requisitos da diretiva, os clientes poderão não conseguir concluir os pagamentos. Encontre mais detalhes no [publicação relacionada do Adobe Commerce DevBlog](https://community.magento.com/t5/Magento-DevBlog/3D-Secure-2-0-changes/ba-p/136460).

## Solução

Siga as recomendações do [Seção Recommendations do Adobe Commerce Payment Provider do DevBlog](https://community.magento.com/t5/Magento-DevBlog/3D-Secure-2-0-changes/ba-p/136460#recommendations).
