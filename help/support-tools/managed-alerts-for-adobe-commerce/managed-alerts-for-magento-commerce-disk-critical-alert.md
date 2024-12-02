---
title: 'Alertas gerenciados para Adobe Commerce: alerta crítico de disco'
description: Este artigo fornece etapas de solução de problemas quando você recebe um alerta de disco crítico para o Adobe Commerce no New Relic. É necessária uma ação imediata para corrigir o problema. O alerta será semelhante ao seguinte, dependendo do canal de notificação de alerta selecionado.
exl-id: 03e5694b-7689-4fbf-8781-636fa46ca0d3
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
source-git-commit: 8b6bf1cdada7edb0cdb0bb3e90ed15ee8cebf77e
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

Você receberá um alerta no New Relic se tiver inscrito no [Managed alerts for Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md) e um ou mais limites de alerta tiverem sido ultrapassados. Esses alertas foram desenvolvidos pela Adobe para fornecer aos clientes um conjunto padrão usando insights do suporte e da engenharia.

<u> **Fazer!** </u>

* Anule qualquer implantação programada até que esse alerta seja limpo.
* Coloque o site no modo de manutenção imediatamente se ele estiver ou se tornar totalmente inoperante. Para obter etapas, consulte [Guia de Instalação > Habilitar ou desabilitar o modo de manutenção](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode). Adicione seu IP à lista de endereços IP isentos para garantir que você ainda possa acessar seu site para solucionar problemas. Para obter as etapas, consulte [Manter a lista de endereços IP isentos](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode#instgde-cli-maint-exempt).

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
>Como este é um alerta crítico, é altamente recomendável concluir a **Etapa 1** antes de tentar solucionar o problema (Etapa 2 em diante).

1. Verifique se existe um tíquete de suporte do Adobe Commerce. Para ver as etapas, consulte [Rastrear seus tíquetes de suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#track-tickets) em nossa knowledge base de suporte. O suporte do pode ter recebido um alerta de limite do New Relic, criado um tíquete e começado a trabalhar no problema. Se não houver nenhum ticket, crie um. O ticket deve ter as seguintes informações:
   * Motivo do contato: selecione &quot;Alerta CRÍTICO New Relic recebido&quot;.
   * Descrição do alerta.
   * [Link do Incidente New Relic](https://docs.newrelic.com/docs/alerts-applied-intelligence/new-relic-alerts/alert-incidents/view-violation-event-details-incidents). Isso está incluído nos seus [Alertas gerenciados para o Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md).
1. No New Relic, examine os discos para maior uso. Para obter etapas, consulte a guia Armazenamento na [página Hosts de monitoramento de infraestrutura:](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#storage) do New Relic
   * Se, no New Relic, você observar um aumento lento no uso do disco, tente as seguintes opções:
   * Otimizando o espaço em disco ajustando a alocação de espaço. Para ver as etapas, consulte [Gerenciar espaço em disco](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space.html) na documentação do desenvolvedor. Talvez também seja necessário solicitar mais espaço em disco (entre em contato com a equipe de conta do Adobe).
   * Libere espaço em disco para o MySQL. Consulte [Pouco espaço em disco do MySQL](/help/troubleshooting/database/mysql-disk-space-is-low-on-magento-commerce-cloud.md) em nossa base de dados de conhecimento de suporte para ver as etapas.
   * Se o New Relic mostrar um rápido aumento do uso do disco, isso pode indicar que há um problema que fez com que um arquivo aumentasse muito rapidamente em um diretório. Faça as seguintes verificações:
1. Verifique o espaço em disco geral para identificar o problema executando o seguinte comando na CLI/Terminal: `df -h`
1. Depois de identificar um diretório com um uso de disco inesperadamente grande e crescente, é necessário verificar o sistema de arquivos afetado. O exemplo a seguir mostra como verificar o diretório de arquivos `pub/media/`. Esse é o diretório que a Commerce usa para armazenar logs e arquivos de mídia grandes. Entretanto, você deve executar este comando para qualquer diretório que mostre uso inesperado do disco: `du -sch ~/pub/media/*`

Se a saída do terminal mostrar um arquivo em um desses diretórios aumentando rapidamente no uso do disco e você souber que o conteúdo do arquivo não é necessário, considere a remoção do arquivo. Se você não se sentir à vontade para realizar esta ação, [envie um tíquete de suporte da Adobe Commerce](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).
