---
title: Aquecimento de cache e site indisponível no Adobe Commerce
description: Este artigo fornece uma solução para quando o cache da página estiver aquecendo e houver uma implantação paralisada ou site inativo.
exl-id: c91d5c1f-95e6-4240-be98-2acea49ae728
feature: Cache, Variables
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
  - id: 8d0b446f-5b16-5a10-b272-01143504a11c
    internal-label: System
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
  - id: 2191e157-828a-5358-ad69-ebcaa8402915
    internal-label: Variables
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '248'
ht-degree: 0%
---
# Aquecimento de cache e site indisponível no Adobe Commerce

Este artigo fornece uma solução para quando o cache da página estiver aquecendo e houver uma implantação paralisada ou site inativo.

## Produtos e versões afetados

* Adobe Commerce na infraestrutura em nuvem, todas as [versões com suporte](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf).

## Problema

O script de aquecimento de cache, no final da fase de pós-implantação, envia solicitações a uma taxa tão alta que determinadas instâncias, como as de 4 cpu, não podem lidar com isso. O nginx deles esgota o número de trabalhadores.

<u>Etapas a serem reproduzidas</u>:

Iniciar operações de aquecimento do cache.

<u>Resultado esperado</u>:

Páginas ou todo o site é carregado.

<u>Resultado real</u>:

O site não está disponível ou o tempo de resposta é muito alto.

## Solução

Limitar o número de conexões simultâneas durante o aquecimento do cache. Isso requer a adição da variável de pós-implantação `WARM_UP_CONCURRENCY` para especificar o número de solicitações de aquecimento que o script de aquecimento de cache pode enviar simultaneamente. Definir essa opção pode ajudar a gerenciar a carga na infraestrutura em nuvem da Adobe Commerce. Para ver as etapas, consulte [Variáveis pós-implantação > WARM\_UP\_CONCURRENCY](https://experienceleague.adobe.com/pt-br/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-post-deploy#warm_up_concurrency) na documentação do desenvolvedor.

## Leitura relacionada

[Cache de Página Inteira](https://experienceleague.adobe.com/pt-br/docs/commerce-admin/systems/tools/cache-management#full-page-caching) em nosso guia do usuário
