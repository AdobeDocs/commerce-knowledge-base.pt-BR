---
title: "Alertas gerenciados no Adobe Commerce: alerta crítico de memória"
description: Este artigo fornece etapas de solução de problemas quando você recebe um alerta crítico de memória para o Adobe Commerce no New Relic. É necessária uma ação imediata para corrigir o problema. O alerta será semelhante ao seguinte, dependendo do canal de notificação de alerta selecionado.
exl-id: feed7998-c50b-4cbf-a92d-cbfc65745a1c
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '961'
ht-degree: 0%

---

# Alertas gerenciados no Adobe Commerce: alerta crítico de memória

Este artigo fornece etapas de solução de problemas quando você recebe um alerta crítico de memória para o Adobe Commerce no New Relic. É necessária uma ação imediata para corrigir o problema. O alerta será semelhante ao seguinte, dependendo do canal de notificação de alerta selecionado.

![alerta crítico de disco](assets/memory-critical-magento-managed.png){width="500"}

## Produtos e versões afetados

Todas as versões da arquitetura do plano Pro da infraestrutura em nuvem do Adobe Commerce.

## Problema

Você receberá um alerta gerenciado no New Relic se tiver inscrito no [Alertas gerenciados para o Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md) e um ou mais limites de alerta tiverem sido ultrapassados. Esses alertas foram desenvolvidos pela Adobe para fornecer aos clientes um conjunto padrão usando insights do suporte e da engenharia.

<u> **Fazer!** </u>

* Anule qualquer implantação agendada até que esse alerta seja limpo
* Coloque o site no modo de manutenção imediatamente se ele estiver ou se tornar totalmente inoperante. Para obter etapas, consulte [Guia de Instalação > Habilitar ou desabilitar o modo de manutenção](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) na documentação do desenvolvedor. Adicione seu IP à lista de endereços IP isentos para garantir que você ainda possa acessar seu site para solucionar problemas. Para ver as etapas, consulte [Manter a lista de endereços IP isentos](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode#instgde-cli-maint-exempt) na documentação do desenvolvedor.

<u>**Não!**</u>

* Inicie campanhas de marketing adicionais que podem trazer visualizações de página adicionais para o site.
* Execute indexadores ou crons adicionais que possam causar tensão adicional na CPU ou no disco.
* Execute qualquer tarefa administrativa importante (ou seja, Commerce Admin, importações/exportações de dados).
* Limpe o cache.

Seu site pode não responder (se você ainda não estiver passando por uma interrupção do site) se você executar uma das ações &quot;Não&quot; antes de investigar e resolver a causa do alerta.

## Solução

Siga estas etapas para identificar e solucionar problemas da causa.

>[!WARNING]
>
>Como este é um alerta crítico, é altamente recomendável concluir a **Etapa 1** antes de tentar solucionar o problema (Etapa 2 em diante).

1. Verifique se existe um tíquete de suporte do Adobe Commerce. Para ver as etapas, consulte [Rastrear seus tíquetes de suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#track-tickets) em nossa knowledge base de suporte. O suporte pode já ter recebido um alerta de limite do New Relic, criado um tíquete e começado a trabalhar no problema. Se não houver nenhum ticket, crie um. O ticket deve ter as seguintes informações:
   * Motivo do contato: selecione &quot;Alerta CRÍTICO New Relic recebido&quot;
   * Descrição do alerta
   * [Link do Incidente New Relic](https://docs.newrelic.com/docs/alerts-applied-intelligence/new-relic-alerts/alert-incidents/view-violation-event-details-incidents). Isso está incluído nos seus [Alertas gerenciados para o Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md).

1. Use a [página Infraestrutura do APM do New Relic](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/) para identificar os principais processos com uso intensivo de memória. Para obter etapas, consulte a [página Hosts de monitoramento de infraestrutura > guia Processos](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#processes) do New Relic:
   * Se serviços como Redis, MySQL ou PHP forem as principais fontes de consumo de memória, tente o seguinte:
1. Verifique se você está usando as versões mais recentes. Às vezes, versões mais recentes podem corrigir vazamentos de memória. Se você não estiver na versão mais recente, considere atualizar. Para obter etapas, consulte [Adobe Commerce na infraestrutura da nuvem > Serviços > Alterar serviços](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/services-yaml.html) em nossa documentação para desenvolvedores.
1. Se o problema com o serviço não estiver relacionado à versão, tente o seguinte:
1. **MySQL**: verifique problemas como consultas de longa execução, chaves primárias não definidas e índices duplicados. Para obter as etapas, consulte [Problemas mais comuns do banco de dados na Adobe Commerce na infraestrutura em nuvem](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/resolve-database-performance-issues.html) em nossa base de dados de conhecimento de suporte.
1. **Redis**: se Redis for a principal fonte de consumo de memória, [envie um tíquete de suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).
1. **PHP**: se o PHP for a principal fonte de consumo de memória, reveja os processos em execução executando o `ps aufx` na CLI/Terminal. Na saída do terminal, você verá processos e trabalhos do CRON que estão sendo executados no momento. Verifique o tempo de execução dos processos na saída. Se houver um cron com um longo tempo de execução, o cron pode estar suspenso. Para obter as etapas de solução de problemas, consulte [Cores de desempenho lento e execução lenta](/help/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons.md) e [Trabalho do Cron preso no status &quot;em execução&quot;](https://support.magento.com/hc/en-us/articles/360033099451) em nossa base de dados de conhecimento de suporte.
1. Se você ainda estiver lutando para identificar a origem do problema, use a [página Transação do APM do New Relic](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems) para identificar transações com problemas de desempenho:
   * Classifique as transações pelas pontuações crescentes do Apdex. [Apdex](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction) refere-se à satisfação do usuário com o tempo de resposta dos seus aplicativos e serviços Web. Uma [baixa pontuação do Apdex](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce-apdex-warning-alert.md) pode indicar um afunilamento (uma transação com um tempo de resposta mais alto). Normalmente é o banco de dados, Redis ou PHP. Para obter etapas, consulte [Exibir transações com a maior insatisfação Apdex](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/view-your-apdex-score#apdex-dissat) da New Relic.
   * Classifique as transações pelo throughput mais alto, o tempo médio de resposta mais lento, o mais demorado e outros limites. Para obter as etapas, consulte o New Relic [Encontrar problemas específicos de desempenho](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems). Se você ainda estiver com dificuldades para identificar o problema, use a página Infraestrutura do APM da New Relic.
1. Se não conseguir identificar a causa do aumento do consumo de memória, analise as tendências recentes para identificar problemas com implantações de código recentes ou alterações de configuração (por exemplo, novos grupos de clientes e grandes alterações no catálogo). É recomendável que você verifique os últimos 7 dias de atividade para obter correlações em implantações ou alterações de código.
1. Se os métodos acima não ajudarem você a encontrar a causa e/ou a solução em um prazo razoável, solicite um upsize ou coloque o site no modo de manutenção, caso ainda não o tenha feito. Para obter as etapas, consulte [Como solicitar o redimensionamento temporário](/help/how-to/general/how-to-request-temporary-magento-upsize.md) em nossa knowledge base de suporte e [Guia de Instalação > Habilitar ou desabilitar o modo de manutenção](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) em nossa documentação de desenvolvedor.
1. Se o upsize retornar o site às operações normais, considere solicitar um upsize permanente (entre em contato com a equipe de conta do Adobe) ou tente reproduzir o problema no ambiente de preparo dedicado executando um teste de carga e otimizando consultas ou código que reduza a pressão sobre os serviços. Consulte [Adobe Commerce na infraestrutura da nuvem > Testar implantação > Teste de carga e estresse](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/test/staging-and-production#load-and-stress-testing) em nossa documentação de desenvolvedor.
