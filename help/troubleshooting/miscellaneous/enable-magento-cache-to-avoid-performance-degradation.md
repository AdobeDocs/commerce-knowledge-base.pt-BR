---
title: Habilite o cache para evitar degradação de desempenho
description: Este artigo explica como resolver um problema de site lento causado pela desativação de determinados tipos de cache do Adobe Commerce.
exl-id: e4e5a753-efa3-4552-aaf6-28e44efcfa5b
feature: Cache, Observability
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4239b8a6-e74f-567d-a7a5-b98b9ead0ea4
    internal-label: Observability
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
source-wordcount: '366'
ht-degree: 0%
---
# Habilite o cache para evitar degradação de desempenho

Este artigo explica como resolver um problema de site lento causado pela desativação de determinados tipos de cache do Adobe Commerce.

## Produtos e versões afetados

* Adobe Commerce na infraestrutura em nuvem 2.2.x, 2.3.x
* Adobe Commerce no local 2.2.x, 2.3.x

## Problema

Você percebe degradação no desempenho. Por exemplo, a página Check-out está carregando lentamente ou o valor Apdex diminui no New Relic.

## Causa

Um motivo para a degradação de desempenho pode ser a desativação de determinados tipos de cache do Adobe Commerce.

## Solução

1. Primeiro, verifique o status do cache do Adobe Commerce para ver se esse é o problema. Para isso, [SSH para o seu ambiente](https://experienceleague.adobe.com/pt-br/docs/commerce-cloud-service/user-guide/develop/secure-connections#ssh) e execute o seguinte comando:

   ```bash
   php bin/magento cache:status
   ```

   Isso exibiria o status de cada tipo de cache (&quot;0&quot; para desativado, &quot;1&quot; para ativado). Ou você pode obter essas informações no arquivo `app/etc/env.php`.

1. Investigue os tipos de cache desabilitados. Todos os tipos de cache do Adobe Commerce devem ser ativados, a menos que você tenha recebido orientações alternativas da Adobe. As extensões de terceiros não devem exigir a desativação do cache do Adobe Commerce.
1. Se a investigação confirmar que alguns tipos de cache estão desabilitados por engano, habilite-os executando o seguinte comando para cada tipo de cache: `php bin/magento cache:enable <your_disabled_cache_type>`

Se houver dúvidas e/ou se um determinado tipo de cache do Adobe Commerce pode ou deve ser desabilitado, [contate o suporte da Adobe Commerce](https://experienceleague.adobe.com/pt-br/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide) solicitando recomendações.

## Leitura relacionada

Documentação do cache do Adobe Commerce na documentação do desenvolvedor:

* [Visão geral do cache do Adobe Commerce](https://developer.adobe.com/commerce/frontend-core/guide/caching)
* [Gerenciar o cache](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/configuration-guide/cli/manage-cache)

Outros motivos possíveis para problemas de desempenho e as soluções para eles:

* [Desative a saída do banner do Adobe Commerce para melhorar o desempenho do site](https://experienceleague.adobe.com/pt-br/docs/experience-cloud-kcs/kbarticles/ka-26909)
* [As tabelas MySQL são muito grandes](https://experienceleague.adobe.com/pt-br/docs/experience-cloud-kcs/kbarticles/ka-26945)
* [Cores lentas, lentas e de longa duração](https://experienceleague.adobe.com/pt-br/docs/experience-cloud-kcs/kbarticles/ka-42802)
