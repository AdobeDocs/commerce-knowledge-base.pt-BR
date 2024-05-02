---
title: "Alertas gerenciados para Adobe Commerce: alerta de aviso da CPU"
description: Este artigo fornece etapas de solução de problemas quando você recebe um alerta de aviso da CPU para o Adobe Commerce no New Relic. É necessária uma ação imediata para corrigir o problema. O alerta será semelhante ao seguinte, dependendo do canal de notificação de alerta selecionado.
exl-id: 03686684-3b7e-430a-a05a-a96f38345322
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
source-git-commit: 324cce66df1e4ab7ec4ef8fb6512c3acbabdf3ab
workflow-type: tm+mt
source-wordcount: '673'
ht-degree: 0%

---

# Alertas gerenciados para Adobe Commerce: alerta de aviso da CPU

Este artigo fornece etapas de solução de problemas quando você recebe um alerta de aviso da CPU para o Adobe Commerce no New Relic. É necessária uma ação imediata para corrigir o problema. O alerta será semelhante ao seguinte, dependendo do canal de notificação de alerta selecionado.

![Alerta de aviso da CPU](assets/cpu-warning-magento-managed.png){width="500"}

## Produtos e versões afetados

Arquitetura do plano Pro da infraestrutura em nuvem do Adobe Commerce

## Problema

Você receberá um alerta no New Relic se tiver se inscrito no [Alertas gerenciados para o Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md) e um ou mais limites de alerta foram ultrapassados. Esses alertas foram desenvolvidos pela Adobe para fornecer aos clientes um conjunto padrão usando insights do suporte e da engenharia.

<u> **Faça!** </u>

* Anule qualquer implantação programada até que esse alerta seja limpo.
* Coloque o site no modo de manutenção imediatamente se ele não responder totalmente. Para obter etapas, consulte [Guia de instalação > Ativar ou desativar o modo de manutenção](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten) na documentação do desenvolvedor. Adicione seu IP à lista de endereços IP isentos para garantir que você ainda possa acessar seu site para solucionar problemas. Para obter etapas, consulte [Manter a lista de endereços IP isentos](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten#instgde-cli-maint-exempt) na documentação do desenvolvedor.

<u>**Não!**</u>

* Inicie campanhas de marketing adicionais que podem trazer visualizações de página adicionais para o site.
* Execute indexadores ou crons adicionais que possam causar tensão adicional na CPU ou no disco.
* Execute qualquer tarefa administrativa importante (ou seja, Commerce Admin, importações/exportações de dados).
* Limpe o cache.

## Solução

Siga estas etapas para identificar e solucionar problemas da causa.

1. Uso [Página de transação do APM do New Relic](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems) para identificar transações com problemas de desempenho:
   * Classifique as transações pelas pontuações crescentes do Apdex. [Apdex](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction) refere-se à satisfação do usuário com o tempo de resposta de seus aplicativos e serviços da web. [Uma pontuação baixa do Apdex](/help/troubleshooting/miscellaneous/troubleshoot-performance-using-new-relic-on-magento-commerce.md#low_user_satisfaction) pode indicar um gargalo (uma transação com um tempo de resposta mais alto). Normalmente é o banco de dados, Redis ou PHP. Para obter etapas, consulte New Relic [Exibir transações com maior insatisfação Apdex](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/view-your-apdex-score#apdex-dissat).
   * Classifique as transações por throughput mais alto, tempo médio de resposta mais lento, mais demorado e outros limites. Para obter etapas, consulte New Relic [Encontrar problemas específicos de desempenho](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems).
1. Se você ainda estiver lutando para identificar a origem, use [Página Infraestrutura APM da New Relic](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/) para identificar serviços de recursos pesados. Para obter etapas, consulte New Relic [Página Monitoramento de infraestrutura: Hosts > tab Processos](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#processes).
1. Se você identificar a origem, o SSH no ambiente para investigar mais detalhadamente. Para obter etapas, consulte [Nuvem para Adobe Commerce > SSH no seu ambiente](https://devdocs.magento.com/cloud/env/environments-ssh.html#ssh) na documentação do desenvolvedor.
1. Se você ainda estiver lutando para identificar a origem:
   * Revise tendências recentes para identificar problemas com implantações de código recentes ou alterações de configuração (por exemplo, novos grupos de clientes e grandes alterações no catálogo). É recomendável que você verifique os últimos sete dias de atividade para obter correlações em implantações ou alterações de código.
   * Considere verificar e desativar catálogos simples. Para obter etapas, consulte [Cores lentas, lentas e de longa duração](/help/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons.md) em nossa base de conhecimento de suporte.
   * Se você suspeitar que esteja enfrentando um ataque de DDoS, tente bloquear o tráfego de bot. Para obter etapas, consulte [Como bloquear tráfego mal-intencionado para Adobe Commerce no nível Fastly](/help/how-to/general/block-malicious-traffic-for-magento-commerce-on-fastly-level.md) em nossa base de conhecimento de suporte.
1. Se o problema parecer temporário, execute etapas de mitigação, como um upsize ou coloque o site no modo de manutenção. Para obter etapas, consulte [Como solicitar redimensionamento temporário](/help/how-to/general/how-to-request-temporary-magento-upsize.md) em nossa base de conhecimento de suporte e [Guia de instalação > Ativar ou desativar o modo de manutenção](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten) na documentação do desenvolvedor. Se o upsize retornar o site às operações normais, considere solicitar um upsize permanente (entre em contato com a equipe de conta do Adobe) ou tente reproduzir o problema no ambiente de preparo dedicado executando um teste de carga e otimizando consultas ou código que reduza a pressão sobre os serviços. Para obter etapas, consulte [Nuvem para Adobe Commerce > Testar implantação > Teste de carga e estresse](https://devdocs.magento.com/cloud/live/stage-prod-test.html#loadtest) na documentação do desenvolvedor.
