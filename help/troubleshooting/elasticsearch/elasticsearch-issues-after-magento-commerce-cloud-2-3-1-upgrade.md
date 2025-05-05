---
title: Problemas de Elasticsearch após a atualização da infraestrutura em nuvem do Adobe Commerce 2.3.1+
description: Este artigo discute uma correção para problemas durante a implantação após a atualização para o Adobe Commerce na infraestrutura em nuvem versões 2.3.1+, se você estiver usando as versões 2.x e 5.x do Elasticsearch.
exl-id: 6ceeb2ea-528d-4c03-ab2b-c5aed46fd0a2
feature: Cloud
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '505'
ht-degree: 0%

---

# Problemas de Elasticsearch após a atualização da infraestrutura em nuvem do Adobe Commerce 2.3.1+

>[!WARNING]
>
>[O mecanismo de pesquisa do catálogo MySQL será removido no Adobe Commerce 2.4.0](/help/announcements/adobe-commerce-announcements/mysql-catalog-search-engine-will-be-removed-in-magento-2-4-0.md). Você deve ter o Elasticsearch host configurado antes de instalar a versão 2.4.0. Consulte [Instalar e configurar o Elasticsearch](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/configuration-guide/search/overview-search).

>[!WARNING]
>
>Observe que as atualizações de serviço não podem ser enviadas para o ambiente de produção sem aviso prévio de 48 horas úteis para nossa equipe de infraestrutura. Isso é necessário, pois precisamos garantir que tenhamos um engenheiro de suporte de infraestrutura disponível para atualizar sua configuração dentro de um prazo desejado com tempo de inatividade mínimo para seu ambiente de produção. Portanto, 48 horas antes de quando suas alterações precisam estar em produção [envie um tíquete de suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) detalhando a atualização de serviço necessária e informando a hora em que deseja que o processo de atualização tenha início.

Este artigo discute uma correção para problemas durante a implantação após a atualização para o Adobe Commerce na infraestrutura em nuvem versões 2.3.1+, se você estiver usando as versões 2.x e 5.x do Elasticsearch.

## Produtos e versões afetados:

* Adobe Commerce na infraestrutura em nuvem 2.3.1+
* Elasticsearch 2.x e 5.x

## Causa

Os comerciantes que atualizaram para o Adobe Commerce na infraestrutura em nuvem (versões 2.3.1 e posteriores) e que estão em uma versão do Elasticsearch anterior à 6.x podem enfrentar erros ao implantar. Isso ocorre porque as versões 2.x e 5.x do Elasticsearch são [Fim da vida útil](https://www.elastic.co/support/eol) e não são mais compatíveis com o Adobe Commerce. O cliente Elasticsearch deve estar atualizado ou a execução de uma implantação pode disparar um erro. Para saber mais, consulte [Alterar o cliente do Elasticsearch](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/configuration-guide/search/overview-search) na documentação do desenvolvedor.

## Problema

Ao implantar, você verá uma mensagem de erro semelhante à seguinte, indicando que a versão do seu Elasticsearch não é compatível: *o serviço de Elasticsearch versão 5.2.2 na camada de infraestrutura não é compatível com a versão atual do módulo elasticsearch/elasticsearch (6.7.0.0), usado pelo seu aplicativo Magento.* *Para corrigir esse problema, atualize o serviço Elasticsearch na infraestrutura do Magento para a versão 6.x*. Outros sintomas desse problema podem ser imagens ausentes e problemas com filtros no ambiente.

## Solução

>[!WARNING]
>
>Se você tiver um ambiente compartilhado, verifique se o preparo e a produção estão prontos para serem atualizados.

Para resolver esse problema, o módulo de cliente Elasticsearch e o serviço de Elasticsearch precisam estar nas versões recomendadas mais recentes:

1. Siga as instruções para [alterar o módulo de Elasticsearch](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/configuration-guide/search/overview-search) na documentação do desenvolvedor para que você tenha a versão mais recente recomendada do módulo de cliente de Elasticsearch.
1. [Envie um tíquete de suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) e solicite uma atualização do serviço Elasticsearch para 6.x em preparo e produção. Observe que uma atualização para o serviço Elasticsearch pode levar algum tempo para ser concluída.

## Leitura relacionada

* [requisitos da pilha de tecnologia do Adobe Commerce 2.3](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/installation-guide/overview) na documentação do desenvolvedor.
* [Configure o serviço Elasticsearch](https://experienceleague.adobe.com/pt-br/docs/commerce-cloud-service/user-guide/configure/service/elasticsearch) na documentação do desenvolvedor.
* [Instale e configure o Elasticsearch](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/configuration-guide/search/overview-search) na documentação do desenvolvedor.
* [Verifique se o Elasticsearch está instalado corretamente](/help/troubleshooting/elasticsearch/ensure-elasticsearch-is-installed-properly.md) em nossa base de dados de conhecimento de suporte.
