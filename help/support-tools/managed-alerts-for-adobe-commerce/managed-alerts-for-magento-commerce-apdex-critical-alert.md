---
title: "Alertas gerenciados para Adobe Commerce: alerta crítico Apdex"
description: Este artigo fornece etapas de solução de problemas quando você recebe um alerta crítico do Apdex para Adobe Commerce no New Relic. A pontuação do Apdex mede a satisfação dos usuários com o tempo de resposta dos aplicativos e serviços Web. É necessária uma ação imediata para corrigir o problema. O alerta será semelhante ao seguinte, dependendo do canal de notificação de alerta selecionado.
exl-id: b6d3d4f3-4abb-4285-8071-2b9fb06bfa3c
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
source-git-commit: fbb24fb3c8b399f3b7e19c663eb4b168657498e6
workflow-type: tm+mt
source-wordcount: '987'
ht-degree: 0%

---

# Alertas gerenciados para Adobe Commerce: alerta crítico Apdex

Este artigo fornece etapas de solução de problemas quando você recebe um alerta crítico do Apdex para Adobe Commerce no New Relic. A pontuação do Apdex mede a satisfação dos usuários com o tempo de resposta dos aplicativos e serviços Web. É necessária uma ação imediata para corrigir o problema. O alerta será semelhante ao seguinte, dependendo do canal de notificação de alerta selecionado.

![alerta crítico apdex](assets/apdex-critical-magento-managed.png){width="500"}

## Produtos e versões afetados

* Arquitetura do plano Pro da infraestrutura em nuvem do Adobe Commerce
* Arquitetura do plano inicial do Adobe Commerce na infraestrutura em nuvem

## Problema

Você receberá um alerta gerenciado no New Relic se tiver se inscrito no [Alertas gerenciados para o Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md) e um ou mais limites de alerta foram ultrapassados. Esses alertas foram desenvolvidos pela Adobe para fornecer aos comerciantes um conjunto padrão usando insights do suporte e da engenharia.

<u> **Faça!** </u>

* Anule qualquer implantação programada até que esse alerta seja limpo.
* Coloque o site no modo de manutenção imediatamente se ele estiver ou se tornar totalmente inoperante. Para obter etapas, consulte [Guia de instalação > Ativar ou desativar o modo de manutenção](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten) na documentação do desenvolvedor. Adicione seu IP à lista de endereços IP isentos para garantir que você ainda possa acessar seu site para solucionar problemas. Para obter etapas, consulte [Manter a lista de endereços IP isentos](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten#instgde-cli-maint-exempt) na documentação do desenvolvedor.

<u>**Não!**</u>

* Inicie campanhas de marketing adicionais que podem trazer visualizações de página adicionais para o site.
* Execute indexadores ou crons adicionais que possam causar tensão adicional na CPU ou no disco.
* Execute qualquer tarefa administrativa importante (ou seja, o Administrador do Commerce, importações/exportações de dados).
* Limpe o cache.

Fazer o que foi descrito acima quando você recebeu um alerta crítico, antes de solucionar a causa do alerta, pode fazer com que o site não responda, caso você ainda não esteja passando por uma interrupção do site.

## Solução

Siga estas etapas para identificar e solucionar problemas da causa.

>[!WARNING]
>
>Como esse é um alerta crítico, é altamente recomendável que você conclua **Etapa 1** antes de tentar solucionar o problema (Etapa 2 em diante).

1. Verifique se existe um tíquete de suporte do Adobe Commerce. Para obter etapas, consulte [Acompanhe seus tíquetes de suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#track-tickets) em nossa base de conhecimento de suporte. O suporte do pode ter recebido um alerta de limite do New Relic, criado um tíquete e começado a trabalhar no problema. Se não houver nenhum ticket, crie um. O ticket deve ter as seguintes informações:
   * Motivo do contato: selecione &quot;Alerta CRÍTICO New Relic recebido&quot;.
   * Descrição do alerta.
   * [Link Incidente New Relic](https://docs.newrelic.com/docs/alerts-applied-intelligence/new-relic-alerts/alert-incidents/view-violation-event-details-incidents). Isso está incluído no seu [Alertas gerenciados para o Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md).
1. Para identificar a origem do problema, use [Página de transação do APM do New Relic](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems) para identificar transações com problemas de desempenho:
   * Classifique as transações pelas pontuações crescentes do Apdex. [Apdex](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction) refere-se à satisfação do usuário com o tempo de resposta de seus aplicativos e serviços da web. Uma pontuação baixa do Apdex pode indicar um gargalo (uma transação com um tempo de resposta mais alto). Normalmente é o banco de dados, Redis ou PHP. Para obter etapas, consulte New Relic [Exibir transações com maior insatisfação Apdex](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction/#dissatisfaction).
   * Classifique as transações pelo throughput mais alto, o tempo médio de resposta mais lento, o mais demorado e outros limites. Para obter etapas, consulte New Relic [Encontrar problemas específicos de desempenho](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems). Se você ainda estiver com dificuldades para identificar o problema, use a página Infraestrutura do APM da New Relic.
1. Uso [Página Infraestrutura APM da New Relic](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/) para identificar processos que consomem muitos recursos. Para obter etapas, consulte New Relic [Página Monitoramento de infraestrutura: Hosts > tab Processos](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#processes).
1. Se serviços como Redis ou MySQL forem a principal fonte de consumo de memória, tente o seguinte:
   * Verifique se você está na versão mais recente. Às vezes, versões mais recentes podem corrigir vazamentos de memória. Se você não estiver na versão mais recente, considere atualizar. Para obter etapas, consulte [Nuvem para Adobe Commerce > Serviços > Alterar serviços](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/services-yaml.html) na documentação do desenvolvedor.
   * Verifique problemas do MySQL, como consultas de longa execução, chaves primárias não definidas e índices duplicados. Para obter etapas, consulte [Problemas mais comuns com o banco de dados no Adobe Commerce na infraestrutura em nuvem](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/resolve-database-performance-issues.html) na documentação do desenvolvedor.
   * Verifique os problemas do PHP. Revisar processos em execução executando `ps aufx` no CLI/Terminal. Na saída do terminal, você verá processos e trabalhos do CRON que estão sendo executados no momento. Verifique o tempo de execução dos processos na saída. Se houver um cron com um longo tempo de execução, o cron pode estar suspenso. Para obter etapas de solução de problemas, consulte [Cores lentas, lentas e de longa duração](/help/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons.md) e [Trabalho Cron paralisado no status &quot;em execução&quot;](/help/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.md) em nossa base de conhecimento de suporte.

1. Depois que a fonte é identificada, SSH entra no ambiente para investigar mais detalhadamente. Para obter etapas, consulte [Nuvem para Adobe Commerce > Tecnologias e requisitos > SSH no seu ambiente](https://devdocs.magento.com/cloud/env/environments-ssh.html#ssh) na documentação do desenvolvedor.
1. Se você ainda estiver lutando para identificar a fonte, revise as tendências recentes para identificar problemas com implantações de código recentes ou alterações de configuração (por exemplo, novos grupos de clientes e grandes alterações no catálogo). É recomendável que você verifique os últimos sete dias de atividade para obter correlações em implantações ou alterações de código.
1. Se você não conseguir encontrar uma solução em um prazo razoável, solicite um upsize ou coloque o site no modo de manutenção se ainda não tiver feito isso. Para obter etapas, consulte [Como solicitar redimensionamento temporário](/help/how-to/general/how-to-request-temporary-magento-upsize.md) em nossa base de conhecimento de suporte e [Guia de instalação > Ativar ou desativar o modo de manutenção](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten) na documentação do desenvolvedor.
1. Se o upsize retornar o site às operações normais, considere solicitar um upsize permanente (entre em contato com a equipe de conta do Adobe) ou tente reproduzir o problema no ambiente de preparo dedicado executando um teste de carga e otimizando consultas ou código que reduza a pressão sobre os serviços. Consulte [Nuvem para Adobe Commerce > Testar implantação > Teste de carga e estresse](https://devdocs.magento.com/cloud/live/stage-prod-test.html#loadtest) na documentação do desenvolvedor.
