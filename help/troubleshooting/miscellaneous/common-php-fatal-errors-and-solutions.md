---
title: Erros fatais comuns do PHP e suas soluções
description: Este artigo lista alguns exemplos rápidos comuns de erros fatais do PHP que você pode encontrar ao procurar nos registros do Adobe Commerce e nas soluções para problemas que eles indicam.
exl-id: 3e42d38f-97bc-4d38-8e36-23b1453f81d9
feature: Support
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
subfeature_v2:
  - id: a59f76dc-e003-5617-951e-dffa5bd3de81
    internal-label: Support
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%
---
# Erros fatais comuns do PHP e suas soluções

Este artigo lista alguns exemplos rápidos comuns de erros fatais do PHP que você pode encontrar ao procurar nos registros do Adobe Commerce e nas soluções para problemas que eles indicam.

## Exemplo

Erro fatal do PHP *: o tempo máximo de execução de 60 segundos foi excedido em...&#39;*

## Solução

Você pode atualizar o tempo máximo de execução definindo um valor `max_execution_time` personalizado no arquivo `php.ini` e reimplantando.

Por exemplo:

`max_execution_time = 120`

Consulte o artigo [Personalizar configurações do php.ini](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/app/php-settings).

## Exemplo

Erro fatal do PHP *: tamanho de memória permitido de 792723456 bytes esgotado&#39;* (Este é apenas um exemplo de tamanho de byte.)

## Solução

Personalize suas configurações do `php.ini`. Consulte este artigo [Personalizar configurações do php.ini](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/app/php-settings).

## Exemplo

&#39;Aviso PHP *: Desconhecido: falha ao abrir fluxo: esse arquivo ou diretório não existe&#39;*

## Solução

Certifique-se de não remover as terminações de estilo Windows no arquivo `php.ini`. No Windows, as terminações de linha são terminadas com uma combinação de um retorno de carro (ASCII 0x0d ou \r) e uma nova linha(\n), também conhecida como CR/LF.

## Exemplo

Erro fatal de PHP de *: PDOException não capturada: SQLSTATE\[HY000\] \[1040\] Muitas conexões em&#39;*

## Solução

O ambiente MySQL ficou sem espaço em disco. Forneça mais espaço em disco para o ambiente MySQL.

## Exemplo

Erro fatal de PHP de *: TypeError não detectado: valor de retorno de Magento&#39;*

## Solução

Verifique o diretório `<root>/tmp` porque ele provavelmente está cheio. Se estiver cheio, forneça mais espaço no diretório. Isso pode envolver simplesmente mover os arquivos para outro diretório ou excluí-los.

## Leitura relacionada

Em nossa documentação do desenvolvedor:

* [Erros de configurações de PHP](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/overview)
* [Configurações necessárias do PHP](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/php-settings)
* [Verificação Redis](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cache/redis/redis-session#verify-redis-connection)
* [Configurar Redis](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cache/redis/config-redis)
* [Erro de limite de memória do PHP](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/overview)
* [Soluções para problemas comuns - Limite de memória](https://developer.adobe.com/commerce/testing/guide/unit/command-line#solutions-to-common-problems)
