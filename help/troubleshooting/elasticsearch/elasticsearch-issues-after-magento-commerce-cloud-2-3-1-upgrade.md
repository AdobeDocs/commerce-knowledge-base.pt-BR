---
title: Problemas de Elasticsearch após a atualização da infraestrutura em nuvem do Adobe Commerce 2.3.1+
description: Este artigo discute uma correção para problemas durante a implantação após a atualização para o Adobe Commerce na infraestrutura em nuvem versões 2.3.1+, se você estiver usando as versões 2.x e 5.x do Elasticsearch.
exl-id: 6ceeb2ea-528d-4c03-ab2b-c5aed46fd0a2
feature: Cloud
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '505'
ht-degree: 0%

---

# Problemas de Elasticsearch após a atualização da infraestrutura em nuvem do Adobe Commerce 2.3.1+

>[!WARNING]
>
>[O mecanismo de pesquisa do catálogo MySQL será removido no Adobe Commerce 2.4.0](/help/announcements/adobe-commerce-announcements/mysql-catalog-search-engine-will-be-removed-in-magento-2-4-0.md). Você deve ter o Elasticsearch host configurado antes de instalar a versão 2.4.0. Consulte [Instalar e configurar o Elasticsearch](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/es-overview.html).

>[!WARNING]
>
>Observe que as atualizações de serviço não podem ser enviadas para o ambiente de produção sem aviso prévio de 48 horas úteis para nossa equipe de infraestrutura. Isso é necessário, pois precisamos garantir que tenhamos um engenheiro de suporte de infraestrutura disponível para atualizar sua configuração dentro de um prazo desejado com tempo de inatividade mínimo para seu ambiente de produção. Portanto, 48 horas antes de quando suas alterações precisam estar em produção [enviar um tíquete de suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) detalhando o upgrade de serviço necessário e informando o horário em que você deseja que o processo de upgrade tenha início.

Este artigo discute uma correção para problemas durante a implantação após a atualização para o Adobe Commerce na infraestrutura em nuvem versões 2.3.1+, se você estiver usando as versões 2.x e 5.x do Elasticsearch.

## Produtos e versões afetados:

* Adobe Commerce na infraestrutura em nuvem 2.3.1+
* Elasticsearch 2.x e 5.x

## Causa

Os comerciantes que atualizaram para o Adobe Commerce na infraestrutura em nuvem (versões 2.3.1 e posteriores) e que estão em uma versão do Elasticsearch anterior à 6.x podem enfrentar erros ao implantar. Isso ocorre porque as versões 2.x e 5.x do Elasticsearch são [Fim da vida útil](https://www.elastic.co/support/eol) e não são mais compatíveis com o Adobe Commerce. O cliente Elasticsearch deve estar atualizado ou a execução de uma implantação pode disparar um erro. Para saber mais, consulte [Alterar o cliente Elasticsearch](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/es-downgrade.html) na documentação do desenvolvedor.

## Problema

Ao implantar, você vê uma mensagem de erro semelhante à seguinte, indicando que a versão do Elasticsearch não é compatível: *O serviço Elasticsearch versão 5.2.2 na camada de infraestrutura não é compatível com a versão atual do módulo elasticsearch/elasticsearch (6.7.0.0), usado pelo aplicativo Magento.*  *Você pode corrigir esse problema atualizando o serviço Elasticsearch na infraestrutura do Magento para a versão 6.x*. Outros sintomas desse problema podem ser imagens ausentes e problemas com filtros no ambiente.

## Solução

>[!WARNING]
>
>Se você tiver um ambiente compartilhado, verifique se o preparo e a produção estão prontos para serem atualizados.

Para resolver esse problema, o módulo de cliente Elasticsearch e o serviço de Elasticsearch precisam estar nas versões recomendadas mais recentes:

1. Siga as instruções para [alterar o módulo Elasticsearch](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/es-downgrade.html) na documentação do desenvolvedor, para que você tenha a versão recomendada mais recente do módulo de cliente Elasticsearch.
1. [Enviar um tíquete de suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) e solicite uma atualização do serviço Elasticsearch para 6.x em preparo e produção. Observe que uma atualização para o serviço Elasticsearch pode levar algum tempo para ser concluída.

## Leitura relacionada

* [Requisitos da pilha de tecnologia do Adobe Commerce 2.3](https://devdocs.magento.com/guides/v2.3/install-gde/system-requirements-tech.html) na documentação do desenvolvedor.
* [Configurar serviço Elasticsearch](https://devdocs.magento.com/cloud/project/project-conf-files_services-elastic.html) na documentação do desenvolvedor.
* [Instalar e configurar o Elasticsearch](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/es-overview.html) na documentação do desenvolvedor.
* [Verifique se o Elasticsearch está instalado corretamente](/help/troubleshooting/elasticsearch/ensure-elasticsearch-is-installed-properly.md) em nossa base de conhecimento de suporte.
