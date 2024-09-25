---
title: Erro ao filtrar pedidos no Administrador
description: Este artigo fornece uma correção para o problema do Adobe Commerce, em que ocorre um erro ao tentar filtrar pedidos no Admin por data, exibindo a mensagem "Violação de restrição de integridade 1052 Coluna 'created_at' onde a cláusula é ambígua".
feature: Orders
role: Developer
source-git-commit: e5eb65b23afaed4658f8576c747f11a31a8ec1aa
workflow-type: tm+mt
source-wordcount: '222'
ht-degree: 0%

---

# Erro ao filtrar pedidos no Administrador

Este artigo fornece um patch para o problema do Adobe Commerce em que ocorre um erro ao tentar filtrar pedidos no Admin por data, exibindo a mensagem: *Violação de restrição de integridade: 1052 Coluna &#39;created_at&#39; onde a cláusula é ambígua*.

## Versões afetadas

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.7

## Problema

Filtrar pedidos no Admin por data retorna um erro.

O exception.log mostra:

```SQL
report.CRITICAL: PDOException: SQLSTATE[23000]: Integrity constraint violation: 1052 Column 'created_at' in where clause is ambiguous in /path/to/magento/vendor/magento/framework/DB/Statement/Pdo/Mysql.php:90
```

<u>Etapas a serem reproduzidas:</u>

1. Vá para **[!UICONTROL Admin]** > **[!UICONTROL Sales]** > **[!UICONTROL Orders]**.
   * Definir a ordem de **[!UICONTROL Purchase Date Ascending]** na grade, OU
   * Definir **[!UICONTROL Purchase Date Filter]** em filtros.

1. Um erro aparece: *Algo deu errado com o processamento do modo de exibição padrão e restauramos o filtro para seu estado original.*

## Causa

Há um problema com os módulos [!DNL PayPal Braintree].

## Solução

Para resolver o problema, aplique o patch anexado a este artigo. Para baixá-lo, role para baixo até o final do artigo e clique no nome do arquivo ou clique no link a seguir:

[bundle_3357_filter_order_in_admin_by_date_patch.zip](assets/bundle-3357-unable-to-filter-order-in-admin-by-date.zip)

O patch é compatível com todas as versões e edições afetadas.

## Como aplicar o patch

Para obter instruções, consulte [Como aplicar um patch de compositor fornecido por Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) na knowledge base de suporte.
