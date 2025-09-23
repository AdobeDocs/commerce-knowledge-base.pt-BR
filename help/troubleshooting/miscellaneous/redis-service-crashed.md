---
title: Falha no serviço Redis
description: O artigo recomenda como consertar o Redis.
exl-id: 5eb8fb70-0f41-433a-8d3f-c368781a2d1d
feature: Services
role: Developer
source-git-commit: 649e01b29b59bf77e6396acbeb7a83bd9c67e1ef
workflow-type: tm+mt
source-wordcount: '222'
ht-degree: 0%

---

# Falha no serviço Redis

O artigo recomenda como consertar o Redis.

## Produtos e versões afetados

* Adobe Commerce na infraestrutura em nuvem 2.2.x., 2.3.x
* Adobe Commerce no local 2.2.x., 2.3x
* Todas as versões do Redis

## Problema

Lentidão ou paralisação do site devido a estouro de memória no Redis.

## Causa

O estouro de memória pode causar falha no serviço Redis. Durante o horário de pico, o serviço Redis pode exigir mais memória do que a alocada no momento.

## Solução

Para verificar a configuração atual e a memória usada, execute o seguinte comando na CLI. Ele verifica a memória usada, maxmemory, chaves removidas e o tempo de atividade do Redis em dias:

```
redis-cli -p REDIS_PORT -h REDIS_HOST info | egrep --color "(role|used_memory_peak|maxmemory|evicted_keys|uptime_in_days)"
```

As variáveis *REDIS\_PORT* e *REDIS\_HOST* podem ser recuperadas de `app/etc/env.php`.

>[!NOTE]
>
>Você também pode recuperar o endereço do host Redis e o número da porta executando este comando da CLI:
>   
>   ```bash
>   echo $MAGENTO_CLOUD_RELATIONSHIPS | base64 -d | json_pp
>   ```


Se a saída da execução da consulta acima mostrar que a porcentagem de memória livre é inferior a 40%, [envie um tíquete ao suporte da Adobe Commerce](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) solicitando um aumento da configuração `maxmemory` no Servidor Redis. Se o valor das chaves removidas não for &quot;0&quot; ou o tempo de atividade do Redis em dias for igual a 0 (indicando que o Redis falhou hoje), você também deve [enviar um tíquete ao suporte da Adobe Commerce](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) solicitando uma investigação e uma correção para esse problema.

## Leitura relacionada

Para saber mais sobre a memória Redis, consulte [Otimização de Memória Redis](https://redis.io/topics/memory-optimization).
