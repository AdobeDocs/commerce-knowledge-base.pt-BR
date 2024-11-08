---
title: Elasticsearch na solução de problemas do Adobe Commerce
description: problemas de Elasticsearch no Adobe Commerce podem ser resolvidos usando a ferramenta solução de problemas de Elasticsearch. Clique em cada pergunta para revelar a resposta em cada etapa da solução de problemas.
exl-id: acae0da0-2918-4021-9fbe-c138940c5a72
feature: Categories
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '992'
ht-degree: 0%

---

# Elasticsearch na solução de problemas do Adobe Commerce

problemas de Elasticsearch no Adobe Commerce podem ser resolvidos usando a ferramenta solução de problemas de Elasticsearch. Clique em cada pergunta para revelar a resposta em cada etapa da solução de problemas.

>[!WARNING]
>
>No Adobe Commerce na infraestrutura em nuvem, observe que as atualizações de serviço não podem ser enviadas para o ambiente de produção sem aviso prévio de 48 horas úteis para nossa equipe de infraestrutura. Isso é necessário, pois precisamos garantir que tenhamos um engenheiro de suporte de infraestrutura disponível para atualizar sua configuração dentro de um prazo desejado com tempo de inatividade mínimo para seu ambiente de produção. Portanto, 48 horas antes de quando suas alterações precisam estar em produção [envie um tíquete de suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) detalhando a atualização de serviço necessária e informando a hora em que deseja que o processo de atualização tenha início.

## Etapa 1 - Verificar problema de Elasticsearch {#step-1}

+++**O problema está relacionado ao Elasticsearch?**

problemas de Elasticsearch indicados por mensagens de erro, &quot;_Nenhum nó ativo encontrado no cluster&quot;,_ produtos ausentes e exibição de informações antigas do produto.

a. SIM - Continue na [Etapa 2](#step-2).\
b. NÃO - Pesquise novamente sobre termos de pesquisa relevantes na [Base de Dados de Conhecimento da Central de Ajuda da Adobe Commerce](https://support.magento.com/hc).

+++

## Etapa 2 - Verificar problema de instalação {#step-2}

+++**É uma nova instalação do Elasticsearch?**

a. SIM - [Verifique se o Elasticsearch está instalado corretamente.](/help/troubleshooting/elasticsearch/ensure-elasticsearch-is-installed-properly.md) Verifique também se você está no Adobe Commerce na infraestrutura em nuvem 2.3.1 ou posterior. Os comerciantes que atualizaram para o Adobe Commerce na infraestrutura em nuvem (versões 2.3.1 e posteriores) e que estão em uma versão do Elasticsearch anterior à 6.x podem enfrentar erros ao implantar. Para resolver esse problema, o módulo de cliente Elasticsearch e o serviço de Elasticsearch precisam estar nas versões recomendadas mais recentes. Para obter as etapas, consulte [problemas de Elasticsearch após a atualização do Adobe Commerce na infraestrutura em nuvem 2.3.1+](/help/troubleshooting/elasticsearch/elasticsearch-issues-after-magento-commerce-cloud-2-3-1-upgrade.md).\
b. NÃO - verifique a integridade do cluster. Se você estiver em um ambiente de preparo ou produção Pro, execute este comando: `curl -m1 localhost:9200/_cluster/health?pretty`. Se você estiver em um ambiente de integração (que inclui todas as ramificações de Início), execute `curl -m1 elasticsearch.internal:9200/_cluster/health?pretty`. Vá para [Etapa 3](#step-3).

+++

## Etapa 3 - Verificar se o cluster de Elasticsearch está disponível {#step-3}

+++**Você recebeu uma resposta do Serviço?**

a. SIM - Continue na [Etapa 4](#step-4).\
b. NÃO - Continue na [Etapa 9](#step-9).

+++

## Etapa 4 - Verificar integridade do cluster de Elasticsearch {#step-4}

+++**Verde de resposta?**

a. SIM - o Elasticsearch está disponível para processar dados e a reindexação deve funcionar. Vá para [Etapa 5](#step-5).\
b. NÃO - Amarelo ou vermelho significa que há problemas com conexões entre nós e alguns dados podem não estar disponíveis. Se estiver amarela, execute o comando: `php bin/magento config:show catalog/search/engine` para verificar o mecanismo de pesquisa. Vá para a [Etapa 6](#step-6). Se estiver vermelho, [envie um tíquete de suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

## Etapa 5 - Verificar funcionamento da pesquisa {#step-5}

+++**Pesquisar problema?**

Os sintomas podem incluir nenhum produto, categorias vazias ou nenhuma atualização de produtos ou categorias de produtos incorreta.

a. SIM - Execute este comando para verificar o status da pesquisa no catálogo: `php bin/magento indexer:status`. Vá para [Etapa 8](#step-8).\
b. NÃO - Execute o comando: `php bin/magento config:show catalog/search/engine`. Vá para a [Etapa 6](#step-6).

+++

## Etapa 6 - Verificar ElasticSuite {#step-6}

+++**ElasticSuite em uso?**

a. SIM - Verifique se o ElasticSuite está na versão atual executando este comando: `cat composer.lock | grep -A 1 elasticsuite | grep '"version"'` Para verificar se esta versão está depreciada ou recomendada, consulte [Github: Smile-SA/elaticsuite](https://github.com/Smile-SA/elasticsuite). Se o ElasticSuite estiver atualizado, prossiga para [Etapa 10](#step-10).\
b. NÃO - prossiga para [Etapa 7](#step-7).

+++

## Etapa 7 - Verificar as ferramentas ECE atualizadas {#step-7}

+++**ECE-tools é a versão mais recente?**

Execute o comando: `php ./vendor/bin/ece-tools -V` e verifique a versão das ferramentas ECE. É a [última versão das ferramentas ECE](https://github.com/magento/ece-tools/releases)?

a. SIM - Continue na [Etapa 5a](#step-5).\
b. NÃO - Atualize as ferramentas ECE para a versão mais recente. Execute o comando `php bin/magento config: show catalog/search/engine` para verificar seu mecanismo de pesquisa. Vá para a [Etapa 6](#step-6).

+++

## Etapa 8 - Verificar reindexação {#step-8}

+++**O status da pesquisa do catálogo está em _Processando_?**

a. SIM - É necessário aguardar até que o processamento seja concluído e, em seguida, verificar se as categorias de produto foram atualizadas. Caso contrário, [envie um tíquete de suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
b. NÃO - Se o status da pesquisa de catálogo for _Reindexação necessária_, execute na CLI/Terminal: `php bin/magento cron:run`. Se isso não funcionar, execute: `php bin/magento indexer:reindex`. Se isso não resolver o problema, [envie um tíquete de suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

## Etapa 9 - Verificar configuração de yaml {#step-9}

+++**`.yaml`arquivo atualizado recentemente?**

a. SIM - Verifique a configuração do Elasticsearch `.yaml` referindo-se ao DevDocs [Configurar Elasticsearch: para habilitar o Elasticsearch](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/service/elasticsearch).\
b. NÃO - [Enviar um tíquete de suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

## Etapa 10 - Verificar índices de rastreamento {#step-10}

+++**Há índices de rastreamento listados?**

Execute `curl elasticsearch.internal:9200/_cat/indices` (se você estiver em um ambiente de integração que inclua todas as ramificações de Início). Se você estiver no ambiente Pro de preparo ou produção, execute `curl localhost:9200/_cat/indices`. Há índices de rastreamento listados? Verifique a saída de `_tracking_log_`.

a. SIM - se você estiver em uma versão do ElasticSuite anterior à versão 2.8.0, é recomendável [atualizar para o ElasticSuite 2.8.0 para ajustar a retenção de índices de rastreamento ou desabilitar o rastreamento](https://support.magento.com/hc/en-us/articles/360035266131?). Se você não puder atualizar imediatamente, [crie um cron para remover os índices de rastreamento](/help/troubleshooting/elasticsearch/elasticsuite-tracking-indices-causes-problems-with-elasticsearch.md). No entanto, isso pode causar problemas de desempenho. Depois de atualizar para o ElasticSuite 2.8.0 ou remover os índices de rastreamento, execute o comando (se estiver em ambientes de preparo ou produção Pro):`localhost:9200/_cat/allocation?v` para verificar o espaço disponível. Se você estiver em um dos ambientes de integração (que inclui todas as ramificações de Início), execute o `elasticsearch.internal:9200/_cat/allocation?v`. Vá para [Etapa 11](#step-11).\
b. NÃO - Se você estiver em ambientes de preparo ou produção Pro, execute o `localhost:9200/_cat/allocation?v` e verifique o espaço disponível. Se você estiver em um dos ambientes de integração (que inclui todas as ramificações de Início), execute o `elasticsearch.internal:9200/_cat/allocation?v`. Vá para [Etapa 11](#step-11).

+++

## Etapa 11 - Pesquisar erro específico {#step-11}

+++**Erro específico?**

Logs, extensões e código personalizado do Adobe Commerce e ES.

a. SIM - Leia o artigo Solução de problemas da Central de ajuda da Adobe Commerce [Verifique se o Elasticsearch está instalado corretamente](/help/troubleshooting/elasticsearch/ensure-elasticsearch-is-installed-properly.md) ou [se há falhas de Elasticsearch ou problemas de memória insuficiente ao usar o plug-in ElasticSuite](https://support.magento.com/hc/en-us/articles/360035266131).\
b. NÃO - Continue na [Etapa 12](#step-12).

+++

## Etapa 12 - Verificar armazenamento disponível {#step-12}

+++**Uso do armazenamento > 85%?**

a. SIM - Você precisa aumentar o armazenamento disponível. Consulte DevDocs[Configurar Elasticsearch: Para habilitar o Elasticsearch](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/service/elasticsearch). Em seguida, execute: `localhost:9200/_cat/allocation?v` (se você estiver em ambientes de preparo ou produção Pro). Se você estiver em um dos ambientes de integração (que inclui todas as ramificações de Início), execute: `elasticsearch.internal:9200/_cat/allocation?v`. Vá para [Etapa 11](#step-11).\
b. NÃO - [Enviar um tíquete de suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

[Voltar à Etapa 1](#step-1)
