---
title: Problemas de desempenho causados por solicitações excessivas do Ajax
description: Este artigo fornece um patch para o problema de desempenho conhecido do Adobe Commerce causado por solicitações excessivas de Ajax. O problema foi corrigido no Adobe Commerce 2.3.4.
exl-id: d9a69406-3970-4556-aa6a-1309b24366d8
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '250'
ht-degree: 0%

---

# Problemas de desempenho causados por solicitações excessivas do Ajax

Este artigo fornece um patch para o problema de desempenho conhecido do Adobe Commerce causado por solicitações excessivas de Ajax. O problema foi corrigido no Adobe Commerce 2.3.4.

## Problema

A Adobe Commerce pode estar enviando dados redundantes [Solicitações do Ajax](/help/troubleshooting/miscellaneous/high-throughput-ajax-requests-cause-poor-performance.md) da loja ao servidor para obter as informações do banner e as informações do cliente. Essas solicitações do Ajax têm um impacto no desempenho, especialmente em condições de alta carga (alto volume e alto tráfego). Portanto, se a funcionalidade Banner não for usada, é recomendável que você [desativar a saída do módulo Adobe Commerce Banner](/help/troubleshooting/miscellaneous/disable-magento-banner-output-to-improve-site-performance.md) e aplique o patch para melhorar a recuperação de informações do cliente.

## Correção

O patch está anexado a este artigo. Para baixá-lo, role para baixo até o final do artigo e clique no nome do arquivo ou clique no link a seguir:

[Baixe o MDVA-24597\_EE\_2.2.9\_COMPOSER\_v1.patch](assets/MDVA-24597_EE_2.2.9_COMPOSER_v1.patch.zip)

### Versões compatíveis do Adobe Commerce

O patch é válido para os seguintes produtos e versões:

* Adobe Commerce na infraestrutura em nuvem 2.2.9
* Adobe Commerce no local 2.2.9

Se você tiver uma versão diferente do Adobe Commerce, considere atualizar para a versão 2.3.x mais recente. Se essa não for uma opção no momento, [entre em contato com o Suporte da Adobe Commerce](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) e solicite um patch para a sua versão.

## Como aplicar o patch

Consulte [Como aplicar um patch de compositor fornecido pelo Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) para obter instruções.

## Arquivos Anexados
