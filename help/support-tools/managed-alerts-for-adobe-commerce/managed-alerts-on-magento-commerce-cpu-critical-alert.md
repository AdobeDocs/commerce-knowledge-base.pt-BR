---
title: 'Alertas gerenciados no Adobe Commerce: alerta crítico de CPU'
description: Este artigo fornece etapas de solução de problemas quando você recebe um alerta crítico de CPU para Adobe Commerce no New Relic. É necessária uma ação imediata para corrigir o problema. O alerta será semelhante ao seguinte, dependendo do canal de notificação de alerta selecionado.
exl-id: 45b8ced0-b12f-428b-9838-2a9c26b9874b
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
source-git-commit: 8b6bf1cdada7edb0cdb0bb3e90ed15ee8cebf77e
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

Você receberá um alerta gerenciado no New Relic se tiver inscrito no [Alertas gerenciados para o Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md) e um ou mais limites de alerta tiverem sido ultrapassados. Esses alertas foram desenvolvidos pela Adobe Commerce para fornecer aos clientes um conjunto padrão usando insights do suporte e da engenharia.

<u>**Fazer!**</u>:

* Anule qualquer implantação programada até que esse alerta seja limpo.
* Coloque o site no modo de manutenção imediatamente se ele estiver ou se tornar totalmente inoperante. Para obter etapas, consulte [Guia de Instalação > Habilitar ou desabilitar o modo de manutenção](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) em nossa documentação para desenvolvedores. Adicione seu IP à lista de endereços IP isentos para garantir que você ainda possa acessar seu site para solucionar problemas. Para ver as etapas, consulte [Manter a lista de endereços IP isentos](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode#instgde-cli-maint-exempt) na documentação do desenvolvedor.

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
>Como este é um alerta crítico, é altamente recomendável concluir a **Etapa 1** antes de tentar solucionar o problema (Etapa 2 em diante).

Verifique se o tíquete de suporte do Adobe Commerce existe. Para ver as etapas, consulte [Rastrear seus tíquetes de suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#track-tickets) em nossa knowledge base de suporte. O suporte do pode ter recebido um alerta de limite do New Relic, criado um tíquete e começado a trabalhar no problema. Se não houver nenhum ticket, crie um. O ticket deve ter as seguintes informações:

1. Motivo do contato: selecione &quot;Alerta CRÍTICO New Relic recebido&quot;.
1. Descrição do alerta.
1. [Link do Incidente New Relic](https://docs.newrelic.com/docs/alerts-applied-intelligence/new-relic-alerts/alert-incidents/view-violation-event-details-incidents). Isso está incluído nos seus [Alertas gerenciados para o Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md).
1. Use a [página Transação de APM do New Relic](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems) para identificar transações com problemas de desempenho:
   * Classifique as transações pelas pontuações crescentes do Apdex. [Apdex](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction) refere-se à satisfação do usuário com o tempo de resposta dos seus aplicativos e serviços Web. Uma [baixa pontuação do Apdex](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce-apdex-warning-alert.md) pode indicar um afunilamento (uma transação com um tempo de resposta mais alto). Normalmente, está relacionado com o banco de dados, Redis, ou PHP. Para obter etapas, consulte [Exibir transações com a maior insatisfação Apdex](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/view-your-apdex-score#apdex-dissat) da New Relic.
   * Classifique as transações por throughput mais alto, tempo médio de resposta mais lento, mais demorado e outros limites. Para obter as etapas, consulte o New Relic [Encontrar problemas específicos de desempenho](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems).
1. Se você ainda estiver com dificuldades para identificar a origem, use a [página Infraestrutura do APM do New Relic](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page) para identificar serviços com muitos recursos. Para obter etapas, consulte a [página Hosts de monitoramento de infraestrutura > guia Processos](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#processes) da New Relic.
1. Se você identificar a origem, o SSH no ambiente para investigar mais detalhadamente. Para ver as etapas, consulte [SSH no seu ambiente para o Adobe Commerce na infraestrutura de nuvem](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html) em nossa documentação de desenvolvedor.
1. Se você ainda estiver lutando para identificar a origem:
   * Revise tendências recentes para identificar problemas com implantações de código recentes ou alterações de configuração (por exemplo, novos grupos de clientes e grandes alterações no catálogo). É recomendável que você verifique os últimos sete dias de atividade para obter correlações em implantações ou alterações de código.
   * Considere verificar e desativar catálogos simples. Para ver as etapas, consulte [Cores de desempenho lento e execução lenta](/help/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons.md) em nossa base de dados de suporte.
   * Se você suspeitar que esteja enfrentando um ataque de DDoS, tente bloquear o tráfego de bot. Para ver as etapas, consulte [Como bloquear tráfego mal-intencionado do Adobe Commerce na infraestrutura em nuvem no nível Fastly](/help/how-to/general/block-malicious-traffic-for-magento-commerce-on-fastly-level.md) em nossa base de conhecimento de suporte.
1. Se o problema parecer temporário, execute etapas de mitigação, como um upsize ou coloque o site no modo de manutenção. Para ver as etapas, consulte [Como solicitar o redimensionamento temporário](/help/how-to/general/how-to-request-temporary-magento-upsize.md) em nossa knowledge base de suporte e [Guia de Instalação > Habilitar ou desabilitar o modo de manutenção](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) em nossa documentação de desenvolvedor. Se o upsize retornar o site às operações normais, considere solicitar um upsize permanente (entre em contato com a equipe de conta do Adobe) ou tente reproduzir o problema no ambiente de preparo dedicado executando um teste de carga e otimizando consultas ou códigos que reduzam a pressão sobre os serviços. Para obter as etapas, consulte [Testar implantação > Teste de carga e estresse](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/test/staging-and-production#load-and-stress-testing) em nossa documentação do desenvolvedor para Adobe Commerce na infraestrutura em nuvem.
