---
title: "Alertas gerenciados para Adobe Commerce: alerta de aviso de memória"
description: Este artigo fornece etapas de solução de problemas para quando você recebe um alerta de aviso de memória do Adobe Commerce no New Relic. É necessária uma ação imediata para corrigir o problema. O alerta será semelhante ao seguinte, dependendo do canal de notificação de alerta selecionado.
exl-id: bb5eb3f4-b162-4737-93d5-4037f2844bb1
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
source-git-commit: 8ef51d4e6d6efa51ad4b328a48b84e10c73f3ac6
workflow-type: tm+mt
source-wordcount: '813'
ht-degree: 0%

---

# Alertas gerenciados para Adobe Commerce: alerta de aviso de memória

Este artigo fornece etapas de solução de problemas para quando você recebe um alerta de aviso de memória do Adobe Commerce no New Relic. É necessária uma ação imediata para corrigir o problema. O alerta será semelhante ao seguinte, dependendo do canal de notificação de alerta selecionado.

![aviso de memória](assets/memory-warning-magento-managed.png){width="500"}

## Produtos e versões afetados

Arquitetura do plano Pro da infraestrutura em nuvem do Adobe Commerce

## Problema

Você receberá um alerta no New Relic se tiver se inscrito no [Alertas gerenciados para o Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md) e um ou mais limites de alerta foram ultrapassados. Esses alertas foram desenvolvidos pela Adobe Commerce para fornecer aos clientes um conjunto padrão usando insights do suporte e da engenharia.

<u>**Faça!**</u>:

* É recomendável suspender qualquer implantação agendada até que esse alerta seja apagado.
* Coloque o site no modo de manutenção imediatamente se ele estiver ou se tornar totalmente inoperante. Para obter etapas, consulte [Guia de instalação > Ativar ou desativar o modo de manutenção](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten) na documentação do desenvolvedor. Adicione seu IP à lista de endereços IP isentos para garantir que você ainda possa acessar seu site para solucionar problemas. Para obter etapas, consulte [Manter a lista de endereços IP isentos](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten#instgde-cli-maint-exempt) na documentação do desenvolvedor.

<u>**Não!**</u>:

* Inicie campanhas de marketing adicionais que podem trazer visualizações de página adicionais para o site.
* Execute indexadores ou crons adicionais, o que pode causar tensão adicional na CPU ou no disco.
* Realize qualquer tarefa administrativa importante (ou seja, o Administrador, importações/exportações de dados).
* Limpe o cache.

## Solução

Siga estas etapas para identificar e solucionar problemas da causa.

1. Uso [Página Infraestrutura APM da New Relic](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/) para identificar os principais processos que consomem muita memória. Para obter etapas, consulte New Relic [Página Monitoramento de infraestrutura: Hosts > tab Processos](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#processes). Se serviços como Redis ou MySQL forem a principal fonte de consumo de memória, tente o seguinte:

   * Verifique se você está na versão mais recente. Às vezes, versões mais recentes podem corrigir vazamentos de memória. Se você não estiver na versão mais recente, considere atualizar. Para obter etapas, consulte [Adobe Commerce na infraestrutura em nuvem > Serviços > Alterar serviços](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/services-yaml.html) na documentação do desenvolvedor.
   * Se ainda não conseguir identificar a origem do aumento do consumo de memória, verifique se há problemas do MySQL, como consultas de longa execução, chaves primárias não definidas e índices duplicados. Para obter etapas, consulte [Problemas mais comuns com o banco de dados no Adobe Commerce na infraestrutura em nuvem](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/resolve-database-performance-issues.html) em nossa base de conhecimento de suporte.
   * Se não houver problemas do MySQL, verifique se há problemas do PHP. Revisar processos em execução executando `ps aufx` no CLI/Terminal. Na saída do terminal, você verá processos e trabalhos do CRON que estão sendo executados no momento. Verifique o tempo de execução dos processos na saída. Se houver um cron com um longo tempo de execução, o cron pode estar suspenso. Consulte [Cores lentos, lentos e de longa duração](/help/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons.md) e [Trabalho Cron paralisado no status &quot;em execução&quot;](/help/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.md) na nossa knowledge base de suporte para obter etapas de solução de problemas.

1. Se você ainda estiver lutando para identificar a origem do problema, use [Página de transação do APM do New Relic](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems) para identificar transações com problemas de desempenho:

   * Classifique as transações pelas pontuações crescentes do Apdex. [Apdex](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction) refere-se à satisfação do usuário com o tempo de resposta de seus aplicativos e serviços da web. A [baixa pontuação do Apdex](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce-apdex-warning-alert.md) pode indicar um gargalo (uma transação com um tempo de resposta mais alto). Normalmente, é o banco de dados, Redis, ou PHP. Para obter etapas, consulte New Relic [Exibir transações com maior insatisfação Apdex](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/view-your-apdex-score#apdex-dissat).
   * Classifique as transações pelo throughput mais alto, o tempo médio de resposta mais lento, o mais demorado e outros limites. Para obter etapas, consulte New Relic [Encontrar problemas específicos de desempenho](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems). Se você ainda estiver com dificuldades para identificar o problema, use a página Infraestrutura do APM da New Relic.

1. Se não conseguir identificar a causa do aumento do consumo de memória, analise as tendências recentes para identificar problemas com implantações de código recentes ou alterações de configuração (por exemplo, novos grupos de clientes e grandes alterações no catálogo). É recomendável que você verifique os últimos sete dias de atividade para obter correlações em implantações ou alterações de código.

1. Se os métodos acima não ajudarem você a encontrar a causa e/ou a solução em um prazo razoável, solicite um upsize ou coloque o site no modo de manutenção, caso ainda não o tenha feito. Para obter etapas, consulte [Como solicitar redimensionamento temporário](/help/how-to/general/how-to-request-temporary-magento-upsize.md) em nossa base de conhecimento de suporte e [Guia de instalação > Ativar ou desativar o modo de manutenção](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten) na documentação do desenvolvedor.

1. Se o upsize retornar o site às operações normais, considere solicitar um upsize permanente (entre em contato com a equipe de conta do Adobe) ou tente reproduzir o problema no ambiente de preparo dedicado executando um teste de carga e otimizando consultas ou código que reduza a pressão sobre os serviços. Consulte [Adobe Commerce na infraestrutura em nuvem > Testar implantação > Teste de carga e estresse](https://devdocs.magento.com/cloud/live/stage-prod-test.html#loadtest) na documentação do desenvolvedor.
