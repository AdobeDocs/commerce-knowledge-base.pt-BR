---
title: Erro '[!DNL Advanced Reporting] 404 no Adobe Commerce'
description: Este artigo fornece uma correção para o problema do Adobe Commerce quando um comerciante recebe um erro 404 ao tentar acessar [[!DNL Advanced Reporting]](https://experienceleague.adobe.com/docs/commerce-admin/config/general/advanced-reporting.html). Após a instalação deste patch, os usuários poderão acessar o  [!DNL Advanced Reporting].
exl-id: bac61704-44fe-4bd2-b342-af90219231ef
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '185'
ht-degree: 0%

---

# [!DNL Advanced Reporting] Erro 404 no Adobe Commerce

Este artigo fornece uma correção para o problema do Adobe Commerce quando um comerciante recebe um erro 404 ao tentar acessar [[!DNL Advanced Reporting]](https://experienceleague.adobe.com/docs/commerce-admin/config/general/advanced-reporting.html). Após a instalação deste patch, os usuários poderão acessar [!DNL Advanced Reporting].

Para verificar se esse patch pode resolver esse problema, revise primeiro os logs usando o seguinte comando:

`zgrep analytics_collect_data var/log/support_report.log var/log/support_report.log.1.gz`

Se você vir o erro `Not valid cipher`, aplique o patch anexado.

## Produtos e versões afetados

Adobe Commerce 2.2.6

## Problema

Um comerciante recebe um erro 404 ao tentar acessar [!DNL Advanced Reporting].

## Solução

Para corrigir o problema, aplique a correção anexada a este artigo. Para baixá-lo, role até o final do artigo e clique no nome do arquivo ou clique no seguinte link: [Baixar MDVA-18980\_EE\_2.2.6\_COMPOSER\_v1](assets/MDVA-18980_EE_2.2.6_COMPOSER_v1.patch.zip)

## Como aplicar o patch

Consulte [Como aplicar um patch de compositor fornecido pelo Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) para obter instruções.

## Arquivos anexados
