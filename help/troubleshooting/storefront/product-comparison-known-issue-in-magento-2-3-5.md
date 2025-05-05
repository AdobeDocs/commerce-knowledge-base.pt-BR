---
title: Problema conhecido de comparação de produto no Adobe Commerce 2.3.5
description: Este artigo fornece recomendações sobre como evitar um problema conhecido [comparação de produto](https://experienceleague.adobe.com/pt-br/docs/commerce-admin/stores-sales/shopper-tools/product-compare) no Adobe Commerce no local 2.3.5 e no Adobe Commerce na infraestrutura em nuvem 2.3.5.
exl-id: 1488e2db-4a5d-4963-b48e-b84f760582d1
feature: Products, Storefront
role: Admin
source-git-commit: b3d39e6b02728f05f046adf7be94ffacbca944d5
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 0%

---

# Problema conhecido de comparação de produto no Adobe Commerce 2.3.5

Este artigo fornece recomendações sobre como evitar um problema conhecido de [comparação de produtos](https://experienceleague.adobe.com/pt-br/docs/commerce-admin/stores-sales/shopper-tools/product-compare) no Adobe Commerce no local 2.3.5 e no Adobe Commerce no Cloud Infrastructure 2.3.5.

## Produtos e versões afetados

* Adobe Commerce no local 2.3.5
* Adobe Commerce na infraestrutura em nuvem 2.3.5

## Problema

Quando um usuário tenta comparar produtos de diferentes visualizações da loja e um produto tem um valor vazio para um atributo comparável, o Adobe Commerce exibe uma página Comparar produtos corrompida.

## Solução

Especifique valores não vazios para atributos de produto comparáveis ou use o valor de exibição de loja padrão para o atributo. Valores de atributo comparáveis não podem estar vazios.

>[!NOTE]
>
>Os atributos do produto estão definidos para serem usados para comparação usando a configuração **Comparável na Loja**. Para obter mais informações, consulte [Criar atributos de produto](https://experienceleague.adobe.com/pt-br/docs/commerce-admin/catalog/product-attributes/create/attribute-product-create#step-4-describe-the-storefront-properties) no guia do usuário.

Uma correção estará disponível no Adobe Commerce 2.3.6, com lançamento previsto para o quarto trimestre de 2020.

Você pode visualizar a correção no GitHub (considere que a correção não passou pelo teste de regressão e não é um hot fix oficial): <https://github.com/magento/magento2/pull/27662>

## Leitura relacionada

<ul><li>Artigos da Base de conhecimento de suporte Adobe Commerce para Adobe Commerce 2.3.5 problemas conhecidos:<ul>
<li>
<p title="Pedidos de vários envios com um produto virtual não processado corretamente no Adobe Commerce 2.3.5"><a href="/help/troubleshooting/miscellaneous/magento-2-3-5-known-issue-virtual-product-multi-ship-orders.md">Pedidos de vários envios com um produto virtual não processado corretamente no Adobe Commerce 2.3.5</a></p>
</li>
<li><a href="/help/troubleshooting/miscellaneous/bulk-action-product-count-known-issue-in-magento-2-3-5.md">Problema conhecido na contagem de produtos da ação em massa no Adobe Commerce 2.3.5</a></li>
<li>
<p title="Correção para o problema de checkout de pagamento do Amazon no Adobe Commerce 2.3.5-p1"><a href="/help/troubleshooting/payments/patch-for-amazon-pay-checkout-issue-in-magento-2-3-5-p1.md">Correção para o problema de checkout de pagamento do Amazon no Adobe Commerce 2.3.5-p1</a></p>
</li>
</ul>
</li><li><a href="https://commerce-docs.github.io/devdocs-archive/2.3/guides/v2.3/release-notes/release-notes-2-3-5-commerce.html#known-issues">Problemas conhecidos do Adobe Commerce 2.3.5</a> em nossa documentação do desenvolvedor</li></ul>
