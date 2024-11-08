---
title: Verifique se o Elasticsearch está instalado corretamente
description: Este artigo fala sobre soluções para problemas causados por instalação e configuração incorreta de Elasticsearch (ES).
exl-id: d2c5971c-4db4-4857-ae79-970313bce981
feature: Install
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '484'
ht-degree: 0%

---

# Verifique se o Elasticsearch está instalado corretamente

Este artigo fala sobre soluções para problemas causados por instalação e configuração incorreta de Elasticsearch (ES).

>[!WARNING]
>
>No Adobe Commerce na infraestrutura em nuvem, observe que as atualizações de serviço não podem ser enviadas para o ambiente de produção sem aviso prévio de 48 horas úteis para nossa equipe de infraestrutura. Isso é necessário, pois precisamos garantir que tenhamos um engenheiro de suporte de infraestrutura disponível para atualizar sua configuração dentro de um prazo desejado com tempo de inatividade mínimo para seu ambiente de produção. Portanto, 48 horas antes de quando suas alterações precisam estar em produção, [envie um tíquete de suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) detalhando a atualização de serviço necessária e informando a hora em que deseja que o processo de atualização tenha início.

## Compatibilidade de versão do Elasticsearch com o Adobe Commerce

* Adobe Commerce no local e Adobe Commerce na infraestrutura em nuvem:
   * A v2.2.3+ é compatível com ES 5.x
   * As versões 2.2.8+ e v2.3.1+ são compatíveis com ES 6.x
   * As versões 2.x e 5.x do ES não são recomendadas devido ao [Fim da vida útil](https://www.elastic.co/support/eol). No entanto, se você tiver o Adobe Commerce v2.3.1 e quiser usar o ES 2.x ou o ES 5.x, você deve [Alterar o Elasticsearch php Client](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/search/overview-search).
* O Magento Open Source v2.3.0+ é compatível com ES 5.x e 6.x (mas recomenda-se o 6.x).

## Problema

Os seguintes sintomas indicam que o Elasticsearch não está configurado corretamente:

* `Error: No alive nodes in your cluster` - este erro pode aparecer nos logs do Adobe Commerce:
   * `var/log/system.log`
   * `var/log/support_report.log`
   * `var/log/cron.log`
   * `var/log/exception.log`
   * ou no prompt (quando você executa uma reindexação, por exemplo)
* Erros que indicam que a versão do Elasticsearch não é compatível com a sua versão atual do Adobe Commerce (este é um erro específico do Adobe Commerce na infraestrutura em nuvem):

  ```
  [YYYY-MM-DD HH:MM:SS] CRITICAL: Fix configuration with given suggestions:    - Elasticsearch version #<version> is not compatible with current version of magento    Upgrade elasticsearch version to ~5.0
  ```

Onde *version* é o Serviço Elasticsearch em execução no ambiente de nuvem.

## Causa

O Elasticsearch não está instalado corretamente. Isso pode ocorrer devido a:

* Um erro de digitação no arquivo de configuração.
* Uma versão no arquivo de configuração que não corresponde a nenhuma versão do Elasticsearch instalada para o ambiente.
* Uma versão instalada corretamente no ambiente, configurada corretamente no arquivo de configuração, mas que não é uma versão compatível com a versão do Adobe Commerce instalada no momento.

## Solução

Para configurar corretamente o Elasticsearch:

* Os comerciantes do Adobe Commerce na infraestrutura em nuvem podem seguir as etapas da documentação do desenvolvedor: [Configurar o serviço Elasticsearch](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/service/elasticsearch).
* Os comerciantes no Adobe Commerce no local e no Magento Open Source podem seguir as etapas da documentação do desenvolvedor: [Instalar e configurar o Elasticsearch](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/search/overview-search).

Após configurar o Elasticsearch, verifique se ele está configurado corretamente:

1. Faça logon no servidor.
1. Verifique o número de versão do Elasticsearch (2.x, 5.x ou 6.x) na saída da execução do comando: `curl -XGET <Elasticsearch hostname>:<Elasticsearch server port>` Por exemplo, no Adobe Commerce na infraestrutura de nuvem: `curl -XGET localhost:9200`
1. Verifique o que está configurado na Configuração do Adobe Commerce na infraestrutura em nuvem executando o comando: `php bin/magento config:show catalog/search`
1. Verifique `catalog/search/engine` e certifique-se de que ele corresponde ao número de versão do Elasticsearch. Por exemplo, no Adobe Commerce, em infraestrutura em nuvem:
   * Elasticsearch 5.X - elasticsearch5
   * Elasticsearch 6.X - elasticsearch6
   * Elasticsearch 2.X - elasticsearch
1. Verificar `index_prefix`. Se você tiver vários ambientes, verifique se tem valores `index_prefix` diferentes para eles.
