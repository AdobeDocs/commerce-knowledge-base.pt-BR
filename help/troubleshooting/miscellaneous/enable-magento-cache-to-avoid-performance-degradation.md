---
title: Habilite o cache para evitar degradação de desempenho
description: Este artigo explica como resolver um problema de site lento causado pela desativação de determinados tipos de cache do Adobe Commerce.
exl-id: e4e5a753-efa3-4552-aaf6-28e44efcfa5b
feature: Cache, Observability
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '290'
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

1. Primeiro, verifique o status do cache do Adobe Commerce para ver se esse é o problema. Para isso, [SSH para o seu ambiente](https://devdocs.magento.com/cloud/env/environments-ssh.html#ssh) e execute o seguinte comando:

   ```bash
   php bin/magento cache:status
   ```

   Isso exibiria o status de cada tipo de cache (&quot;0&quot; para desativado, &quot;1&quot; para ativado). Ou você pode obter essas informações no arquivo `app/etc/env.php`.

1. Investigue os tipos de cache desabilitados. Todos os tipos de cache do Adobe Commerce devem ser ativados, a menos que você tenha recebido orientações alternativas do Adobe. As extensões de terceiros não devem exigir a desativação do cache do Adobe Commerce.
1. Se a investigação confirmar que alguns tipos de cache estão desabilitados por engano, habilite-os executando o seguinte comando para cada tipo de cache: `php bin/magento cache:enable <your_disabled_cache_type>`

Se houver dúvidas e/ou se um determinado tipo de cache do Adobe Commerce pode ou deve ser desabilitado, [contate o suporte da Adobe Commerce](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) solicitando recomendações.

## Leitura relacionada

Documentação do cache do Adobe Commerce na documentação do desenvolvedor:

* [visão geral do cache do Adobe Commerce](https://devdocs.magento.com/guides/v2.3/frontend-dev-guide/cache_for_frontdevs.html)
* [Gerenciar o cache](https://devdocs.magento.com/guides/v2.3/config-guide/cli/config-cli-subcommands-cache.html)

Outros motivos possíveis para problemas de desempenho e as soluções para eles:

* [Desative a saída do banner do Adobe Commerce para melhorar o desempenho do site](/help/troubleshooting/miscellaneous/disable-magento-banner-output-to-improve-site-performance.md)
* [As tabelas MySQL são muito grandes](/help/troubleshooting/database/mysql-tables-are-too-large.md)
* [Cores lentas, lentas e de longa duração](/help/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons.md)
* [Acesso de administrador restrito que causa problemas de desempenho](/help/troubleshooting/miscellaneous/restricted-admin-access-causing-performance-issues.md)
