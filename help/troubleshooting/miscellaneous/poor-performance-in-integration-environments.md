---
title: Baixo desempenho em ambientes de integração
description: Este artigo fornece uma solução para o problema em que os ambientes de integração Pro e os ambientes de preparo de Início têm um desempenho insatisfatório.
feature: Integration, Staging
role: Developer
exl-id: 46110dbc-2f54-4654-95e2-39e8ae1e6979
source-git-commit: 139c2836ba36686357c7a5458a36550c7b1273c1
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 0%

---

# Baixo desempenho em ambientes de integração

Este artigo fornece uma solução para o problema em que os ambientes de integração Pro e os ambientes de preparo de Início têm um desempenho insatisfatório.

## Produtos e versões afetados:

* Adobe Commerce na infraestrutura em nuvem (todas as versões)

## Problema

Seu ambiente de integração Pro ou ambiente de preparo de Início está com baixo desempenho.

## Causa

Dependendo do tamanho do catálogo/dados ou dos requisitos de integrações/personalizações de terceiros, os recursos disponíveis nos ambientes de integração podem ter excedido.

## Solução

Para resolver problemas de desempenho, siga as práticas recomendadas para melhor desempenho no ambiente de integração. Talvez também seja necessário solicitar uma atualização dos ambientes para aprimorar a integração.

Primeiro, determine se seu ambiente está na [configuração da Integração aprimorada](https://experienceleague.adobe.com/pt-br/docs/experience-cloud-kcs/kbarticles/ka-27242).

* [Arquitetura Pro](https://experienceleague.adobe.com/pt-br/docs/commerce-cloud-service/user-guide/architecture/pro-architecture#integration-environment)
* [Arquitetura de Início](https://experienceleague.adobe.com/pt-br/docs/commerce-cloud-service/user-guide/architecture/starter-architecture#staging-environment)

Verifique o log de implantação usando um desses métodos.

### Método 1:

Execute o seguinte comando usando a CLI da nuvem:

`magento-cloud activity:log -e <branch name>`

### Método 2:

Verifique o log de implantação mais recente para esse ambiente no [Cloud Console](https://console.adobecommerce.com).

No final do log de implantação, se você vir algo assim, a primeira linha mostra size=XL e as linhas restantes mostram size=L, isso significa que você está na configuração da Integração aprimorada.

```
Environment configuration
mymagento (type: php:8.2, size: XL, disk: 5120)
mysql (type: mysql:10.6, size: L, disk: 5120)
redis (type: redis:7.2, size: L)
opensearch (type: opensearch:2, size: L, disk: 1024)
rabbitmq (type: rabbitmq:3.12, size: L, disk: 1024)
```

Se você não estiver na configuração da Integração aprimorada, poderá [solicitar a melhoria/atualização](https://experienceleague.adobe.com/pt-br/docs/experience-cloud-kcs/kbarticles/ka-27242).
Se você já estiver na configuração da Integração aprimorada ou ainda encontrar problemas de desempenho após a atualização, siga as práticas recomendadas para obter o desempenho ideal no ambiente de integração:

* [Arquitetura Pro](https://experienceleague.adobe.com/pt-br/docs/commerce-cloud-service/user-guide/architecture/pro-architecture#integration-environment)
* [Arquitetura de Início](https://experienceleague.adobe.com/pt-br/docs/commerce-cloud-service/user-guide/architecture/starter-architecture#staging-environment)

Se você atendeu às recomendações acima, [envie uma solicitação de suporte](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#submit-ticket) para obter assistência adicional.
