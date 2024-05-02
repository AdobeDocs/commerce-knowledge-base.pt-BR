---
title: "Alertas gerenciados para Adobe Commerce: alerta crítico de disco"
description: Este artigo fornece etapas de solução de problemas quando você recebe um alerta de disco crítico para o Adobe Commerce no New Relic. É necessária uma ação imediata para corrigir o problema. O alerta será semelhante ao seguinte, dependendo do canal de notificação de alerta selecionado.
exl-id: 03e5694b-7689-4fbf-8781-636fa46ca0d3
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
source-git-commit: c829b4383fa808df29aab03229c59f06ef8a38bc
workflow-type: tm+mt
source-wordcount: '669'
ht-degree: 0%

---

# Alertas gerenciados para Adobe Commerce: alerta crítico de disco

Este artigo fornece etapas de solução de problemas quando você recebe um alerta de disco crítico para o Adobe Commerce no New Relic. É necessária uma ação imediata para corrigir o problema. O alerta será semelhante ao seguinte, dependendo do canal de notificação de alerta selecionado.

![alerta crítico de disco](assets/disk-critical-magento-managed.png){width="500"}

## Produtos e versões afetados

Infraestrutura em nuvem do Adobe Commerce na arquitetura de plano Pro

## Problema

Você receberá um alerta no New Relic se tiver se inscrito no [Alertas gerenciados para o Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md) e um ou mais limites de alerta foram ultrapassados. Esses alertas foram desenvolvidos pela Adobe para fornecer aos clientes um conjunto padrão usando insights do suporte e da engenharia.

<u> **Faça!** </u>

* Anule qualquer implantação programada até que esse alerta seja limpo.
* Coloque o site no modo de manutenção imediatamente se ele estiver ou se tornar totalmente inoperante. Para etapas, consulte [Guia de instalação > Ativar ou desativar o modo de manutenção](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten) . Adicione seu IP à lista de endereços IP isentos para garantir que você ainda possa acessar seu site para solucionar problemas. Para obter etapas, consulte [Manter a lista de endereços IP isentos](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten#instgde-cli-maint-exempt).

**Não!**

* Inicie campanhas de marketing adicionais que podem trazer visualizações de página adicionais para o site.
* Execute indexadores ou crons adicionais que possam causar tensão adicional na CPU ou no disco.
* Execute qualquer tarefa administrativa importante (ou seja, Commerce Admin, importações/exportações de dados).
* Limpe o cache.

Seu site pode não responder (se você ainda não estiver passando por uma interrupção do site) se você executar uma das ações &quot;Não&quot; antes de investigar e resolver a causa do alerta.

## Solução

Siga estas etapas para identificar e solucionar problemas da causa.

>[!WARNING]
>
>Como esse é um alerta crítico, é altamente recomendável que você conclua **Etapa 1** antes de tentar solucionar o problema (Etapa 2 em diante).

1. Verifique se existe um tíquete de suporte do Adobe Commerce. Para obter etapas, consulte [Acompanhe seus tíquetes de suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#track-tickets) em nossa base de conhecimento de suporte. O suporte do pode ter recebido um alerta de limite do New Relic, criado um tíquete e começado a trabalhar no problema. Se não houver nenhum ticket, crie um. O ticket deve ter as seguintes informações:
   * Motivo do contato: selecione &quot;Alerta CRÍTICO New Relic recebido&quot;.
   * Descrição do alerta.
   * [Link Incidente New Relic](https://docs.newrelic.com/docs/alerts-applied-intelligence/new-relic-alerts/alert-incidents/view-violation-event-details-incidents). Isso está incluído no seu [Alertas gerenciados para o Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md).
1. No New Relic, examine os discos para maior uso. Para obter etapas, consulte a guia Armazenamento no New Relic [Página Hosts de Monitoramento de Infraestrutura:](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#storage)
   * Se, no New Relic, você observar um aumento lento no uso do disco, tente as seguintes opções:
   * Otimizando o espaço em disco ajustando a alocação de espaço. Para obter etapas, consulte [Gerenciar espaço em disco](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space.html) na documentação do desenvolvedor. Talvez também seja necessário solicitar mais espaço em disco (entre em contato com a equipe de conta do Adobe).
   * Libere espaço em disco para o MySQL. Consulte [O espaço em disco do MySQL é insuficiente](/help/troubleshooting/database/mysql-disk-space-is-low-on-magento-commerce-cloud.md) na nossa base de conhecimento de suporte para etapas.
   * Se o New Relic mostrar um rápido aumento do uso do disco, isso pode indicar que há um problema que fez com que um arquivo aumentasse muito rapidamente em um diretório. Faça as seguintes verificações:
1. Verifique o espaço total em disco para identificar o problema executando o seguinte comando na CLI/Terminal: `df -h`
1. Depois de identificar um diretório com um uso de disco inesperadamente grande e crescente, é necessário verificar o sistema de arquivos afetado. O exemplo a seguir mostra como verificar o diretório de arquivos `pub/media/`. Esse é o diretório que a Commerce usa para armazenar logs e arquivos de mídia grandes. No entanto, você deve executar este comando para qualquer diretório que mostre uso inesperado do disco: `du -sch ~/pub/media/*`

Se a saída do terminal mostrar um arquivo em um desses diretórios aumentando rapidamente no uso do disco e você souber que o conteúdo do arquivo não é necessário, considere a remoção do arquivo. Se você não se sentir à vontade para realizar essa ação, [enviar um tíquete de suporte do Adobe Commerce](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).
