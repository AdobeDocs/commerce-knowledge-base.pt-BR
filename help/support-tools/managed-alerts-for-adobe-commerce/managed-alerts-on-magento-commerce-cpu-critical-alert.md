---
title: "Alertas gerenciados no Adobe Commerce: alerta crítico da CPU"
description: Este artigo fornece etapas de solução de problemas quando você recebe um alerta crítico de CPU para Adobe Commerce no New Relic. É necessária uma ação imediata para corrigir o problema. O alerta será semelhante ao seguinte, dependendo do canal de notificação de alerta selecionado.
exl-id: 45b8ced0-b12f-428b-9838-2a9c26b9874b
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
source-git-commit: 5be8f2969426078bfcc0e4ffb4895dcf0327165f
workflow-type: tm+mt
source-wordcount: '823'
ht-degree: 0%

---

# Alertas gerenciados no Adobe Commerce: alerta crítico de CPU

Este artigo fornece etapas de solução de problemas quando você recebe um alerta crítico de CPU para Adobe Commerce no New Relic. É necessária uma ação imediata para corrigir o problema. O alerta será semelhante ao seguinte, dependendo do canal de notificação de alerta selecionado.

![alerta crítico de disco](assets/cpu-critical-magento-managed.png){width="500"}

## Produtos e versões afetados

Arquitetura do plano Pro da infraestrutura em nuvem do Adobe Commerce

## Problema

Você receberá um alerta gerenciado no New Relic se tiver se inscrito no [Alertas gerenciados para o Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md) e um ou mais limites de alerta foram ultrapassados. Esses alertas foram desenvolvidos pela Adobe Commerce para fornecer aos clientes um conjunto padrão usando insights do suporte e da engenharia.

<u>**Faça!**</u>:

* Anule qualquer implantação programada até que esse alerta seja limpo.
* Coloque o site no modo de manutenção imediatamente se ele estiver ou se tornar totalmente inoperante. Para obter etapas, consulte [Guia de instalação > Ativar ou desativar o modo de manutenção](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten) na documentação do desenvolvedor. Adicione seu IP à lista de endereços IP isentos para garantir que você ainda possa acessar seu site para solucionar problemas. Para obter etapas, consulte [Manter a lista de endereços IP isentos](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten#instgde-cli-maint-exempt) na documentação do desenvolvedor.

<u>**Não!**</u>:

* Inicie campanhas de marketing adicionais que podem trazer visualizações de página adicionais para o site.
* Execute indexadores ou crons adicionais, o que pode causar tensão adicional na CPU ou no disco.
* Execute qualquer tarefa administrativa importante (ou seja, o Administrador do Commerce, importações/exportações de dados).
* Limpe o cache.

Seu site pode não responder (se você ainda não estiver passando por uma interrupção do site) se você executar qualquer uma das ações &quot;Não&quot; antes de investigar e resolver a causa do alerta.

## Solução

Siga estas etapas para identificar e solucionar problemas da causa.

>[!WARNING]
>
>Como esse é um alerta crítico, é altamente recomendável que você conclua **Etapa 1** antes de tentar solucionar o problema (Etapa 2 em diante).

Verifique se o tíquete de suporte do Adobe Commerce existe. Para obter etapas, consulte [Acompanhe seus tíquetes de suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#track-tickets) em nossa base de conhecimento de suporte. O suporte do pode ter recebido um alerta de limite do New Relic, criado um tíquete e começado a trabalhar no problema. Se não houver nenhum ticket, crie um. O ticket deve ter as seguintes informações:

1. Motivo do contato: selecione &quot;Alerta CRÍTICO New Relic recebido&quot;.
1. Descrição do alerta.
1. [Link Incidente New Relic](https://docs.newrelic.com/docs/alerts-applied-intelligence/new-relic-alerts/alert-incidents/view-violation-event-details-incidents). Isso está incluído no seu [Alertas gerenciados para o Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md).
1. Uso [Página de transação do APM do New Relic](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems) para identificar transações com problemas de desempenho:
   * Classifique as transações pelas pontuações crescentes do Apdex. [Apdex](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction) refere-se à satisfação do usuário com o tempo de resposta de seus aplicativos e serviços da web. A [baixa pontuação do Apdex](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce-apdex-warning-alert.md) pode indicar um gargalo (uma transação com um tempo de resposta mais alto). Normalmente, está relacionado com o banco de dados, Redis, ou PHP. Para obter etapas, consulte New Relic [Exibir transações com maior insatisfação Apdex](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/view-your-apdex-score#apdex-dissat).
   * Classifique as transações por throughput mais alto, tempo médio de resposta mais lento, mais demorado e outros limites. Para obter etapas, consulte New Relic [Encontrar problemas específicos de desempenho](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems).
1. Se você ainda estiver lutando para identificar a origem, use [Página Infraestrutura APM da New Relic](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page) para identificar serviços que consomem muitos recursos. Para obter etapas, consulte New Relic [Página Monitoramento de infraestrutura: Hosts > tab Processos](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#processes).
1. Se você identificar a origem, o SSH no ambiente para investigar mais detalhadamente. Para obter etapas, consulte [SSH em seu ambiente para Adobe Commerce na infraestrutura em nuvem](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html) na documentação do desenvolvedor.
1. Se você ainda estiver lutando para identificar a origem:
   * Revise tendências recentes para identificar problemas com implantações de código recentes ou alterações de configuração (por exemplo, novos grupos de clientes e grandes alterações no catálogo). É recomendável que você verifique os últimos sete dias de atividade para obter correlações em implantações ou alterações de código.
   * Considere verificar e desativar catálogos simples. Para obter etapas, consulte [Cores lentas, lentas e de longa duração](/help/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons.md) em nossa base de conhecimento de suporte.
   * Se você suspeitar que esteja enfrentando um ataque de DDoS, tente bloquear o tráfego de bot. Para obter etapas, consulte [Como bloquear tráfego mal-intencionado para o Adobe Commerce na infraestrutura em nuvem no nível Fastly](/help/how-to/general/block-malicious-traffic-for-magento-commerce-on-fastly-level.md) em nossa base de conhecimento de suporte.
1. Se o problema parecer temporário, execute etapas de mitigação, como um upsize ou coloque o site no modo de manutenção. Para obter etapas, consulte [Como solicitar redimensionamento temporário](/help/how-to/general/how-to-request-temporary-magento-upsize.md) em nossa base de conhecimento de suporte e [Guia de instalação > Ativar ou desativar o modo de manutenção](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten) na documentação do desenvolvedor. Se o upsize retornar o site às operações normais, considere solicitar um upsize permanente (entre em contato com a equipe de conta do Adobe) ou tente reproduzir o problema no ambiente de preparo dedicado executando um teste de carga e otimizando consultas ou códigos que reduzam a pressão sobre os serviços. Para obter etapas, consulte [Testar implantação > Teste de carga e estresse](https://devdocs.magento.com/cloud/live/stage-prod-test.html#loadtest) em nossa documentação de desenvolvedor para Adobe Commerce na infraestrutura em nuvem.
