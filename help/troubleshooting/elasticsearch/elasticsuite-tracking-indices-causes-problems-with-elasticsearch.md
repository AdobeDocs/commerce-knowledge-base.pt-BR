---
title: Os índices de rastreamento do ElasticSuite causam problemas com o Elasticsearch
description: Este artigo fala sobre a questão de problemas de memória de Elasticsearch causados por índices de rastreamento produzidos pelo plug-in ElasticSuite.
exl-id: 67bfd06a-c801-4306-8510-a84a6fe5351a
source-git-commit: c1c2bd29e14f4cbfffb235801e95ec7cbb7c7a55
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 0%

---

# Os índices de rastreamento do ElasticSuite causam problemas com o Elasticsearch

>[!NOTE]
>
>O ElasticSuite e seus aplicativos afiliados são ferramentas de terceiros atualmente não compatíveis com o Adobe. Esse conteúdo está sendo apresentado apenas como informação e não como uma indicação do que está habilitado para a cobertura de suporte.

Este artigo fala sobre a questão de problemas de memória de Elasticsearch causados por índices de rastreamento produzidos pelo plug-in ElasticSuite.

## Produtos e versões afetados

As versões do ElasticSuite anteriores à 2.8.0 não podem limpar periodicamente os índices de rastreamento.

As versões do ElasticSuite anteriores à 2.9.8/2.10.7 estão armazenando índices de rastreamento em índices diários, o que faz com que o número de índices abertos aumente.

## Problema

Se o plug-in de terceiros ElasticSuite estiver instalado, você pode ter problemas de memória de Elasticsearch e o serviço de Elasticsearch pode travar devido aos índices de rastreamento do ElasticSuite. Os sintomas incluem:

* O Elasticsearch trava sem erros de memória.
* Ao executar um comando de funcionamento `curl -m1 localhost:9200/_cluster/health?pretty` ou `curl -m1 elasticsearch.internal:9200/_cluster/health?pretty` (para contas iniciais) existem centenas ou milhares de `unassigned_shards`
* O desempenho do Elasticsearch ou do site foi gravemente degradado.
* *&quot;Nenhum nó ativo encontrado no cluster&quot;* em erros de implantação ou registro de Elasticsearch.
* *&quot;Rejeição da atualização de mapeamento em [&lt;\*>_ tracking_log_event _&lt;\*>]&quot;* em erros de implantação ou de log.

## Causa

O ElasticSuite tem um novo recurso que cria índices de rastreamento. Esses índices de rastreamento registram quais termos de pesquisa são os mais usados, quais termos geram mais faturamento e quais termos estão levando a uma página sem resultados, para que os comerciantes possam criar sinônimos para corrigi-los. Parece que não exclui os índices de rastreamento, portanto, o Elasticsearch fica sem recursos e falha.

## Solução

### Atualize sua versão do ElasticSuite para limpar os índices de rastreamento periodicamente

Depois de atualizar o plug-in ElasticSuite para uma versão superior a 2.8.0, você pode configurar uma limpeza periódica dos índices.

Ir para **Lojas** > **Configuração** > **Rastreamento** > **Configuração global** > **Atraso de retenção**

O período de retenção padrão é de 365 dias. Você pode reduzi-la para 30 ou 15 dias.

### Atualize sua versão do ElasticSuite para usar índices mensais em vez de índices diários

Depois de atualizar o plug-in ElasticSuite para a versão > 2.9.8/2.10.7, os índices de rastreamento serão mensais.

Você ainda pode reduzir o período de retenção:

Ir para **Lojas** > **Configuração** > **Rastreamento** > **Configuração global** > **Atraso de retenção**

O período de retenção padrão é de 12 meses (gerará 12 índices). Você pode reduzi-lo para 3 ou 6 meses.

### Usar um cronjob para limpar os dados dos índices de rastreamento

Crie um trabalho cron para excluir os índices de rastreamento. Esse comando exclui índices criados no mês passado:

```
   curl -XDELETE localhost:9200/<name in index> * **\_tracking\_log** * _$(date
    +'%Y%m' -d 'last month')*
```

Se você deseja excluir índices em uma frequência de tempo definida, crie um trabalho cron referenciando os seguintes artigos em nossa documentação do desenvolvedor:

* [Configurar um trabalho cron personalizado e um grupo cron (tutorial)](https://devdocs.magento.com/guides/v2.3/config-guide/cron/custom-cron-tut.html)
* [Configurar trabalhos cron](https://devdocs.magento.com/guides/v2.3/cloud/configure/setup-cron-jobs.html)
