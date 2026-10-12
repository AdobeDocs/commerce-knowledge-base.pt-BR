---
title: 'ERRO: falha no aquecimento do Adobe Commerce na infraestrutura de nuvem'
description: 'Este artigo fornece uma solução para quando o cache da página está sendo aquecido e falha com um erro:'
exl-id: 20a88030-b1c9-4fdc-83c1-f344d44cd2e1
feature: Cache, Cloud, Paas
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 5a951749-fac9-5bc7-9a98-ebe4ff066437
    internal-label: Cloud
  - id: 00451af3-7b97-5414-9992-3a6c269e413f
    internal-label: Paas
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '213'
ht-degree: 0%
---
# ERRO: falha no aquecimento do Adobe Commerce na infraestrutura de nuvem

Este artigo fornece uma solução para quando o cache da página está sendo aquecido e falha com um erro:

*ERRO: Falha no aquecimento:`<website link>`*

## Produtos e versões afetados

* Adobe Commerce na infraestrutura em nuvem, todas as [versões com suporte](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Problema

Falha no aquecimento de cache.

<u>Etapas a serem reproduzidas</u>:

Iniciar operações de aquecimento do cache.

<u>Resultado esperado</u>:

Páginas ou todo o site é carregado.

<u>Resultado real</u>:

O site não está disponível ou o tempo de resposta é muito alto. *ERRO: Falha no aquecimento:`<website link>`*

## Causa

O aquecimento de cache não funciona com o controle de acesso HTTP ativado.

## Solução

Verifique se o controle de acesso está habilitado: vá para a ramificação/ambiente específico, clique no ícone **Configurações** e verifique a configuração **Controle de acesso HTTP** - o aquecimento do cache não pode ocorrer neste cenário e o controle de acesso deve ser desabilitado.

## Leitura relacionada

* [Guia do Usuário do Adobe Commerce > Cache de Página Inteira](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/cache-management#full-page-caching) em nosso guia do usuário.
* [Aquecimento de cache e site não disponível no Adobe Commerce](/help/troubleshooting/miscellaneous/cache-warming-up-and-site-unavailable-on-magento.md) em nossa base de dados de conhecimento de suporte.
