---
title: O Adobe Commerce solicita que os clientes façam logon em um link inválido
description: O artigo fornece um link para o patch de um problema conhecido do Adobe Commerce 2.3.5, em que os clientes são solicitados a fazer logon, mas o link para reenviar um email de confirmação não funciona.
exl-id: 8adef44f-56a6-4f57-a9b5-fb8583d8ae8d
feature: Logs
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '278'
ht-degree: 0%

---

# O Adobe Commerce solicita que os clientes façam logon em um link inválido

O artigo fornece um link para o patch de um problema conhecido do Adobe Commerce 2.3.5, em que os clientes são solicitados a fazer logon, mas o link para reenviar um email de confirmação não funciona.

## Produtos e versões afetados

* Adobe Commerce (todos os métodos de implantação) 2.3.5

## Problema

A Adobe Commerce solicita que os clientes façam logon exibindo esta mensagem: *&quot;Esta conta não foi confirmada. Clique aqui para reenviar o email de confirmação &quot;*. O link **Clique aqui** deve abrir a página Enviar link de confirmação, mas está inativo.

## Solução

Uma correção para esse problema está disponível nos Recursos Técnicos da Adobe Commerce: [Reenviar correção de problema de link de email de confirmação de conta para o Adobe Commerce 2.3.5](https://magento.com/tech-resources/download?_ga=2.193540264.409362045.1590506265-807369446.1578680711#download2368). Uma correção permanente estará disponível no Adobe Commerce 2.3.6, com lançamento previsto para o quarto trimestre de 2020.

Consulte [Como aplicar um patch de compositor fornecido pelo Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) para obter instruções sobre como aplicar um patch de compositor.

## Leitura relacionada

Artigos da nossa base de conhecimento de suporte e documentação do desenvolvedor sobre problemas conhecidos do Adobe Commerce 2.3.5:

* [Problema conhecido do Adobe Commerce 2.3.5: pedidos virtuais de vários envios](/help/troubleshooting/miscellaneous/magento-2-3-5-known-issue-virtual-product-multi-ship-orders.md)
* [Problema conhecido de comparação de produto no Adobe Commerce 2.3.5](/help/troubleshooting/storefront/product-comparison-known-issue-in-magento-2-3-5.md)
* [Correção 2.3.5, 2.3.5-p1 do Adobe Commerce: problema de pagamento do país](/help/troubleshooting/known-issues-patches-attached/magento-2-3-5-2-3-5-p1-patch-country-payment-issue.md)
* [O Adobe Commerce solicita que os clientes façam logon em um link inválido](/help/troubleshooting/known-issues-patches-attached/magento-prompts-customers-log-in-invalid-link.md)
* [Problema conhecido na contagem de produtos da ação em massa no Adobe Commerce 2.3.5](/help/troubleshooting/miscellaneous/bulk-action-product-count-known-issue-in-magento-2-3-5.md)
* [Correção para o problema de checkout de pagamento do Amazon no Adobe Commerce 2.3.5-p1](/help/troubleshooting/payments/patch-for-amazon-pay-checkout-issue-in-magento-2-3-5-p1.md)
* [Problemas conhecidos do Adobe Commerce 2.3.5](https://devdocs.magento.com/guides/v2.3/release-notes/release-notes-2-3-5-commerce.html#known-issues)
