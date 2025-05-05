---
title: Erros fatais comuns do PHP e suas soluções
description: Este artigo lista alguns exemplos rápidos comuns de erros fatais do PHP que você pode encontrar ao procurar nos registros do Adobe Commerce e nas soluções para problemas que eles indicam.
exl-id: 3e42d38f-97bc-4d38-8e36-23b1453f81d9
feature: Support
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '291'
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

Consulte o artigo [Personalizar configurações do php.ini](https://experienceleague.adobe.com/pt-br/docs/commerce-cloud-service/user-guide/configure/app/php-settings).

## Exemplo

Erro fatal do PHP *: tamanho de memória permitido de 792723456 bytes esgotado&#39;* (Este é apenas um exemplo de tamanho de byte.)

## Solução

Personalize suas configurações do `php.ini`. Consulte este artigo [Personalizar configurações do php.ini](https://experienceleague.adobe.com/pt-br/docs/commerce-cloud-service/user-guide/configure/app/php-settings).

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

* [erros de configurações do PHP](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/troubleshooting/overview)
* [Configurações de PHP necessárias](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/installation-guide/prerequisites/php-settings)
* [Verificação Redis](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/configuration-guide/cache/redis/redis-session#verify-redis-connection)
* [Configurar Redis](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/configuration-guide/cache/redis/config-redis)
* [Erro de limite de memória do PHP](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/troubleshooting/overview)
* [Soluções para problemas comuns - Limite de memória](https://developer.adobe.com/commerce/testing/guide/unit/command-line/#solutions-to-common-problems)
