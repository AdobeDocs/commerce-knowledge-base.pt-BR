---
title: Não é possível validar o número de IVA - Adobe Commerce na infraestrutura em nuvem
description: Este artigo fornece uma correção para o problema em que há um erro durante a verificação do número IVA.
exl-id: 9868e888-bad8-4823-acab-4b3804933cb0
feature: Cloud, Customer Service, Paas
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '224'
ht-degree: 0%

---

# Não é possível validar o número de IVA - Adobe Commerce na infraestrutura em nuvem

Este artigo fornece uma correção para o problema em que há um erro durante a verificação do número IVA.

## Produtos e versões afetados

Todas as versões do Adobe Commerce no local e do Adobe Commerce na infraestrutura em nuvem até a 2.3.6 (incluindo 2.3.5-p1) foram afetadas, incluindo as versões p1 e p2 já lançadas. Isso inclui:

* 2.3.5-p1
* 2.3.5
* 2.3.4 - 2.3.4-p2
* 2.3.3 - 2.3.3-p1
* 2.3.2 -2.3.2-p2
* 2.0.0 - 2.3.1

## Problema

<u>Etapas a serem reproduzidas:</u>

1. Ir para **Lojas** > **Configuração** > **Clientes** > **Configuração do cliente** > **Criar novas opções de conta** e defina **Ativar atribuição automática** para **Grupo de Clientes** para *Sim*.
1. Ir para **Geral** > **Armazenar informações** > e defina um País e um Número de IVA válidos.
1. Clique em **Validar Número IVA**.

<u>Resultado esperado:</u>

Validação bem-sucedida.

<u>Resultado real:</u>

O seguinte erro é exibido: &quot;*Erro durante a verificação do número IVA.*&quot;

## Solução

Aplique o [correção](assets/MDVA-27623_EE_2.3.2-p2_COMPOSER_v1.patch.zip) artigo.

## Correção

O patch está anexado a este artigo. Para baixá-lo, role para baixo até o final do artigo e clique no nome do arquivo ou clique no link a seguir:

[MDVA-27623\_EE\_2.3.2-p2\_COMPOSER\_v1.patch](assets/MDVA-27623_EE_2.3.2-p2_COMPOSER_v1.patch.zip)

## Como aplicar o patch

Consulte [Como aplicar um patch de compositor fornecido pelo Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) para obter instruções.

## Arquivos Anexados
