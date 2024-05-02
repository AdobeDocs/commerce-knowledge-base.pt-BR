---
title: Verifique os registros para solucionar problemas de erros 500 e 503 no Adobe Commerce
description: Este artigo explica como verificar o "access.log" e os logs relacionados para solucionar problemas de erros 503 e 500, que podem ser causados por tráfego ou recursos insuficientes do servidor. A visualização do "access.log" e logs relacionados pode fornecer informações sobre o que pode estar causando problemas relacionados ao Adobe Commerce na infraestrutura da nuvem.
exl-id: 47d7de6b-3e12-4e79-a5c1-c27a9196b99c
feature: Cloud, Logs
source-git-commit: f11c8944b83e294b61d9547aefc9203af344041d
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 0%

---

# Verifique os registros para solucionar problemas de erros 500 e 503 no Adobe Commerce

Este artigo explica como verificar a `access.log` e logs relacionados para solucionar problemas de erros 503 e 500, que podem ser causados por tráfego ou recursos insuficientes do servidor. Exibir o `access.log` Os logs relacionados podem fornecer informações sobre o que pode estar causando problemas relacionados ao Adobe Commerce na infraestrutura em nuvem.

<!--
Bob - not in TOC
-->

## Produtos e versões afetados

* Adobe Commerce na infraestrutura em nuvem, tudo [versões compatíveis](https://experienceleague.adobe.com/docs/commerce-operations/release/planning/lifecycle-policy.html).

Para visualizar os registros desses erros de servidor, verifique a `access.log` no servidor Web, por exemplo, `<ip address>` `<timestamp>` `<request uri>` `<response code>` `<referer url>`

Para verificar logs relacionados:

1. Execute o seguinte comando na CLI se ele estiver no dia atual (para a arquitetura de plano Adobe Commerce na infraestrutura em nuvem Pro). Ou até um certo ponto no passado (para a arquitetura de plano inicial da infraestrutura em nuvem do Adobe Commerce), já que a duração da cobertura dos logs é limitada e a rotação de logs não está disponível: `grep -r "\" [50[0-9]" /path/to/access.log` Se o erro ocorreu no passado, execute o seguinte comando na CLI (somente arquitetura Pro): `zgrep "\" 50[0-9]" /path/to/access.log.<rotation ID>.gz`
1. Verifique a `exception.log` e `error.log` ou equivalente [log girado](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/next-steps/configuration.html#log-rotation) (logs que são automaticamente girados e compactados quando atingem um determinado tamanho de arquivo) para o mesmo carimbo de data e hora para localizar o erro em potencial e ver o que pode estar ocorrendo para causá-lo. Observação: para verificar a `exception.log` e `error.log` execute os comandos acima na CLI, mas substitua `access.log` com `exception.log` ou `error.log`.

## Leitura relacionada

* Consulte [Exibir e gerenciar logs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html) no *Guia da infraestrutura do Adobe Commerce na nuvem*.
* Consulte [Solução de problemas de erros 503](/help/troubleshooting/miscellaneous/troubleshooting-503-errors.md) em nossa base de conhecimento de suporte.
* Consulte [Solução de problemas de site Magento inativo](/help/troubleshooting/site-down-or-unresponsive/magento-site-down-troubleshooter.md) em nossa base de conhecimento de suporte.
