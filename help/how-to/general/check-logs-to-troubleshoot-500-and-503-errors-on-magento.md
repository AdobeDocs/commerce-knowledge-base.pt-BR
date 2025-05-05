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

Este artigo explica como verificar o `access.log` e os logs relacionados para solucionar problemas de erros 503 e 500, que podem ser causados por tráfego ou recursos insuficientes do servidor. A exibição de `access.log` e logs relacionados pode fornecer informações sobre o que pode estar causando problemas relacionados ao Adobe Commerce na infraestrutura de nuvem.

<!--
Bob - not in TOC
-->

## Produtos e versões afetados

* Adobe Commerce na infraestrutura em nuvem, todas as [versões com suporte](https://experienceleague.adobe.com/docs/commerce-operations/release/planning/lifecycle-policy.html?lang=pt-BR).

Para exibir logs para esses erros de servidor, verifique o `access.log` no servidor Web, por exemplo, `<ip address>` `<timestamp>` `<request uri>` `<response code>` `<referer url>`

Para verificar logs relacionados:

1. Execute o seguinte comando na CLI se ele estiver no dia atual (para a arquitetura de plano Adobe Commerce na infraestrutura em nuvem Pro). Ou até um certo ponto no passado (para a arquitetura de plano de Início da infraestrutura em nuvem do Adobe Commerce), já que a duração da cobertura dos logs é limitada e a rotação de logs não está disponível: `grep -r "\" [50[0-9]" /path/to/access.log` Se o erro tiver ocorrido no passado, execute o seguinte comando na CLI (somente arquitetura Pro): `zgrep "\" 50[0-9]" /path/to/access.log.<rotation ID>.gz`
1. Em seguida, verifique o `exception.log` e `error.log` ou o [log girado](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/next-steps/configuration.html?lang=pt-BR#log-rotation) equivalente (logs que são automaticamente girados e compactados quando atingem determinado tamanho de arquivo) para obter o mesmo carimbo de data e hora para localizar o erro potencial e ver o que pode estar ocorrendo para causá-lo. Observação: para verificar o `exception.log` e o `error.log`, execute os comandos acima na CLI, mas substitua `access.log` por `exception.log` ou `error.log`.

## Leitura relacionada

* Consulte [Exibir e gerenciar logs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html?lang=pt-BR) no *Guia do Adobe Commerce on Cloud Infrastructure*.
* Consulte [Solução de problemas de erros 503](/help/troubleshooting/miscellaneous/troubleshooting-503-errors.md) em nossa knowledge base de suporte.
* Consulte o [Solucionador de problemas de site inativo](/help/troubleshooting/site-down-or-unresponsive/magento-site-down-troubleshooter.md) do Magento em nossa base de dados de conhecimento de suporte.
