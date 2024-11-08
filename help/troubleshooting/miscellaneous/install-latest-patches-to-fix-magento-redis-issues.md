---
title: Instale os patches mais recentes para corrigir problemas do Adobe Commerce Redis
description: Este artigo fornece informações sobre os patches mais recentes relacionados ao Redis disponíveis no pacote [Adobe Commerce on cloud infrastructure Patches](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches).
exl-id: 0335bc11-f679-4629-b4e7-6a0e68c3ae44
feature: Cache, Install, Services
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 0%

---

# Instale os patches mais recentes para corrigir problemas do Adobe Commerce Redis

Este artigo fornece informações sobre os patches mais recentes relacionados ao Redis disponíveis no pacote [Adobe Commerce on cloud infrastructure Patches](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches).

## Produtos e versões afetados

Adobe Commerce na infraestrutura em nuvem 2.3.3, 2.3.4

## Problema

O consumo extra de CPU e memória pela Redis pode diminuir o desempenho do Adobe Commerce e, portanto, o desempenho geral do seu site.

## Solução

Aplique os patches mais recentes fornecidos pelo Adobe Commerce no pacote de Patches da infraestrutura em nuvem. Para obter instruções detalhadas, consulte [Aplicar patches](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) na documentação do desenvolvedor.

Os patches mais recentes do Redis fornecidos pela Adobe Commerce no pacote de patches da infraestrutura em nuvem contribuem para o seguinte:

* reduzindo o tamanho da comunicação em rede para Redis
* correção das condições de corrida que levam ao consumo extra de memória
* alterando o adaptador de cache para cobrir casos de remoção
* diminuindo o consumo de CPU do Redis

A Adobe Commerce também recomenda atualizar para o Redis 5, se você estiver executando o Adobe Commerce na infraestrutura em nuvem 2.3.3 ou superior.
