---
title: O Google Analytics não está rastreando dados de conversão
description: Este artigo fornece uma correção para o problema conhecido do Adobe Commerce 2.2.4 relacionado ao não rastreamento dos dados de conversão pelos Google Analytics.
exl-id: b9012fd1-4f90-41e9-9559-0343ee052ec6
feature: Configuration, Observability
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '280'
ht-degree: 0%

---

# O Google Analytics não está rastreando dados de conversão

Este artigo fornece uma correção para o problema conhecido do Adobe Commerce 2.2.4 relacionado ao não rastreamento dos dados de conversão pelos Google Analytics.

>[!NOTE]
>
>O problema foi corrigido no Adobe Commerce 2.2.6.

## Problema

Os dados de conversão não foram rastreados pelo Google Analytics devido a um erro no código do componente Google Analytics.

<u>Etapas a serem reproduzidas</u>:

1. Habilite e configure a funcionalidade de Google Analytics no Administrador do Commerce em **Lojas** > **Configurações** > **Configuração** > **Vendas** > **API do Google** > **Google Analytics**.
1. Clique em **Salvar configuração**.
1. Faça um pedido na vitrine.
1. Vá para **Painel de Google Analytics** > **Conversões** > **Visão geral**.
1. Defina o intervalo de datas para a data atual.

<u>Resultado esperado</u>:

A ordem é exibida nos dados de conversão.

<u>Resultado real</u>:

A ordem não aparece nos dados de conversão.

## Solução

O patch corrige o erro no código do componente Google Analytics. Após a aplicação, os dados de conversão de patch serão rastreados por Google Analytics.

## Correção

O patch está anexado a este artigo. Para baixá-lo, role para baixo até o final do artigo e clique no nome do arquivo ou clique no link a seguir:

[Baixar MDVA-11263\_EE\_2.2.4\_v1.composer.patch](assets/MDVA-11263_EE_2.2.4_v1.composer.patch.zip)

### Versões compatíveis do Adobe Commerce:

A correção foi criada para:

* Adobe Commerce no local 2.2.4

O patch também é compatível (mas pode não resolver o problema) com as seguintes versões e edições do Adobe Commerce:

* Adobe Commerce no local 2.2.5
* Adobe Commerce na infraestrutura em nuvem 2.2.4, 2.2.5

## Como aplicar o patch

Consulte [Como aplicar um patch de compositor fornecido pelo Adobe Commerce](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) para obter instruções.

## Arquivos Anexados
