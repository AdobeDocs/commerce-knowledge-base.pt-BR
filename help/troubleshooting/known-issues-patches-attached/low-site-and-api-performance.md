---
title: Baixo desempenho do site e da API
description: Este artigo fornece um patch para o problema conhecido do Adobe Commerce na infraestrutura em nuvem 2.2.1 relacionado ao baixo desempenho do site e da API causado por um longo tempo necessário para gravar "debug.log".
exl-id: b71816cd-f580-4c80-9694-585ed051a56d
feature: REST, Observability
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 0%

---

# Baixo desempenho do site e da API

Este artigo fornece um patch para o problema conhecido do Adobe Commerce na infraestrutura em nuvem 2.2.1 relacionado ao baixo desempenho do site e da API causado por um longo tempo necessário para gravar `debug.log`.

## Problema

O desempenho do site está lento. As operações da API são executadas lentamente, por exemplo, atualização de produtos usando o `PUT` método. Quando você observa as operações de maneira mais detalhada usando o New Relic, a maior parte da memória e da CPU é consumida ao gravar em `/var/log/debug.log`.

## Solução

Para resolver o problema, aplique o patch. O patch divide e grava os registros de métodos de registro, pagamento e envio em arquivos separados.

## Correção

O patch está anexado a este artigo. Para baixá-lo, role para baixo até o final do artigo e clique no nome do arquivo ou clique no link a seguir:

[Baixar MDVA-8371\_EE\_2.2.1\_COMPOSER\_v2.patch](assets/MDVA-8371_EE_2.2.1_COMPOSER_v2.patch.zip)

### Versões compatíveis do Adobe Commerce

A correção foi criada para:

* Adobe Commerce na infraestrutura em nuvem 2.2.1

O patch também é compatível (mas pode não resolver o problema) com as seguintes versões e edições do Adobe:

* Adobe Commerce na infraestrutura em nuvem 2.2.0, 2.2.2, 2.2.3
* Adobe Commerce no local 2.2.0, 2.2.2, 2.2.3

## Como aplicar o patch

Consulte [Como aplicar um patch de compositor fornecido pelo Adobe Commerce](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) na nossa base de conhecimento de suporte para obter instruções.

## Arquivos Anexados
