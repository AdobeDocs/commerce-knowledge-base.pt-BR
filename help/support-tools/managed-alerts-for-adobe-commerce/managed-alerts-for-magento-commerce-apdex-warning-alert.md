---
title: 'Alertas gerenciados para Adobe Commerce: alerta de aviso Apdex'
description: Este artigo fornece etapas de solução de problemas para quando você recebe um alerta de aviso do Apdex para o Adobe Commerce no New Relic. A pontuação do Apdex mede a satisfação dos usuários com o tempo de resposta dos aplicativos e serviços Web. É necessária uma ação imediata para corrigir o problema. O alerta será semelhante ao seguinte, dependendo do canal de notificação de alerta selecionado.
exl-id: 6e3f28ae-734b-468f-b6a5-c4f2edb1cb4b
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '851'
ht-degree: 0%

---

# Alertas gerenciados para Adobe Commerce: alerta de aviso Apdex

Este artigo fornece etapas de solução de problemas para quando você recebe um alerta de aviso do Apdex para o Adobe Commerce no New Relic. A pontuação do Apdex mede a satisfação dos usuários com o tempo de resposta dos aplicativos e serviços Web. É necessária uma ação imediata para corrigir o problema. O alerta será semelhante ao seguinte, dependendo do canal de notificação de alerta selecionado.

![alerta de aviso do apdex](assets/apdex-warning-magento-managed.png){width="500"}

## Produtos e versões afetados

* Arquitetura do plano Pro da infraestrutura em nuvem do Adobe Commerce
* Arquitetura do plano inicial do Adobe Commerce na infraestrutura em nuvem

## Problema

Você receberá um alerta gerenciado no New Relic se tiver inscrito no [Alertas gerenciados para o Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md) e um ou mais limites de alerta tiverem sido ultrapassados. Esses alertas foram desenvolvidos pela Adobe para fornecer aos comerciantes um conjunto padrão usando insights do suporte e da engenharia.

<u> **Fazer!** </u>

* Anule qualquer implantação programada até que esse alerta seja limpo.
* Coloque o site no modo de manutenção imediatamente se ele estiver ou se tornar totalmente inoperante. Para obter etapas, consulte [Guia de Instalação > Habilitar ou desabilitar o modo de manutenção](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) em nossa documentação para desenvolvedores. Adicione seu IP à lista de endereços IP isentos para garantir que você ainda possa acessar seu site para solucionar problemas. Para ver as etapas, consulte [Manter a lista de endereços IP isentos](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode#instgde-cli-maint-exempt) na documentação do desenvolvedor.

<u>**Não!**</u>

* Inicie campanhas de marketing adicionais que podem trazer visualizações de página adicionais para o site.
* Execute indexadores ou crons adicionais que possam causar tensão adicional na CPU ou no disco.
* Execute qualquer tarefa administrativa importante (ou seja, Commerce Admin, importações/exportações de dados).
* Limpe o cache.

## Solução

Siga estas etapas para identificar e solucionar problemas da causa.

1. Para identificar a origem do problema, use a [página Transação do APM do New Relic](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems) para identificar transações com problemas de desempenho:
   * Classifique as transações pelas pontuações crescentes do Apdex. [Apdex](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction) refere-se à satisfação do usuário com o tempo de resposta dos seus aplicativos e serviços Web. Uma [baixa pontuação do Apdex](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce-apdex-warning-alert.md) pode indicar um afunilamento (uma transação com um tempo de resposta mais alto). Normalmente é o banco de dados, Redis ou PHP. Para obter etapas, consulte [Exibir transações com a maior insatisfação Apdex](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/view-your-apdex-score#apdex-dissat) da New Relic.
   * Classifique as transações pelo throughput mais alto, o tempo médio de resposta mais lento, o mais demorado e outros limites. Para obter as etapas, consulte o New Relic [Encontrar problemas específicos de desempenho](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems).
1. Use a [página Infraestrutura do APM do New Relic](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/) para identificar processos que consomem muitos recursos. Para obter etapas, consulte a [página Hosts de monitoramento de infraestrutura > guia Processos](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#processes) da New Relic.
1. Se serviços como Redis ou MySQL forem a principal fonte de consumo de memória, tente o seguinte:
   * Verifique se você está na versão mais recente. Às vezes, versões mais recentes podem corrigir vazamentos de memória. Se você não estiver na versão mais recente, considere atualizar. Para obter etapas, consulte [Cloud para Adobe Commerce > Serviços > Alterar serviços](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/services-yaml.html) em nossa documentação do desenvolvedor.
1. Se o problema não for causado pelas versões do serviço:
   * Verifique outros problemas do MySQL, como consultas de longa execução, chaves primárias não definidas e índices duplicados. Para obter as etapas, consulte [Problemas mais comuns do banco de dados na Adobe Commerce na infraestrutura em nuvem](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/resolve-database-performance-issues.html) em nossa base de dados de conhecimento de suporte.
   * Verifique outros problemas do PHP. Revise os processos em execução executando `ps aufx` na CLI/Terminal. Na saída do terminal, você verá processos e trabalhos do CRON que estão sendo executados no momento. Verifique o tempo de execução dos processos na saída. Se houver um cron com um longo tempo de execução, o cron pode estar suspenso. Para obter as etapas de solução de problemas, consulte [Cores de desempenho lento e execução demorada](/help/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons.md) e [Trabalho do Cron preso no status &quot;em execução&quot;](/help/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.md) em nossa base de dados de suporte.
1. Depois que uma possível fonte do problema é identificada, o SSH entra no ambiente para investigar mais detalhadamente. Para ver as etapas, consulte [Cloud para Adobe Commerce > Tecnologias e requisitos > SSH no seu ambiente](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/secure-connections#ssh) na documentação do desenvolvedor.
1. Se você ainda estiver lutando para identificar a fonte, revise as tendências recentes para identificar problemas com implantações de código recentes ou alterações de configuração (por exemplo, novos grupos de clientes e grandes alterações no catálogo). É recomendável que você verifique os últimos sete dias de atividade para obter correlações em implantações ou alterações de código.
1. Se você não conseguir encontrar uma solução em um prazo razoável, solicite um upsize ou coloque o site no modo de manutenção se ainda não tiver feito isso. Para ver as etapas, consulte [Como solicitar o redimensionamento temporário](/help/how-to/general/how-to-request-temporary-magento-upsize.md) em nossa knowledge base de suporte e [Guia de Instalação > Habilitar ou desabilitar o modo de manutenção](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) em nossa documentação de desenvolvedor.
1. Se o [upsize](/help/how-to/general/how-to-request-temporary-magento-upsize.md) retornar o site para operações normais, considere solicitar um upsize permanente (entre em contato com a equipe de conta do Adobe) ou tente reproduzir o problema no ambiente de preparo dedicado executando um teste de carga e otimizando consultas, ou código que reduza a pressão sobre os serviços. Consulte [Cloud para Adobe Commerce > Implantação de teste > Teste de carga e estresse](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/test/staging-and-production#load-and-stress-testing) em nossa documentação de desenvolvedor.
