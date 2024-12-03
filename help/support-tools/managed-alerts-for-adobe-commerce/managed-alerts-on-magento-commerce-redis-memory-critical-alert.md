---
title: 'Alertas gerenciados no Adobe Commerce: alerta crítico de memória Redis'
description: Este artigo fornece etapas de solução de problemas para quando você receber um alerta crítico de memória Redis para Adobe Commerce no New Relic. É necessária ação imediata para resolver o problema. O alerta será semelhante ao seguinte, dependendo do canal de notificação de alerta selecionado.
exl-id: 28e1d879-d7ca-4439-8e81-52a1fbf3ecb0
feature: Cache, Categories, Observability, Services, Support, Tools and External Services, Variables
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '690'
ht-degree: 0%

---

# Alertas gerenciados no Adobe Commerce: alerta crítico de memória Redis

Este artigo fornece etapas de solução de problemas para quando você receber um alerta crítico de memória Redis para Adobe Commerce no New Relic. É necessária ação imediata para resolver o problema. O alerta será semelhante ao seguinte, dependendo do canal de notificação de alerta selecionado.

![new_relic_redis_memory_critical.png](assets/new_relic_redis_memory_critical.png)

## Produtos e versões afetados

Todas as versões da arquitetura de plano Pro da infraestrutura em nuvem do Adobe Commerce

## Problema

Você receberá um alerta no New Relic se tiver inscrito no [Managed alerts for Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md) e um ou mais limites de alerta tiverem sido ultrapassados. Esses alertas foram desenvolvidos pela Adobe para fornecer aos comerciantes um conjunto padrão de alertas usando insights do suporte e da engenharia.

**<u>Fazer!</u>**

* Anule qualquer implantação programada até que esse alerta seja limpo.
* Coloque o site no modo de manutenção imediatamente se ele estiver ou se tornar totalmente inoperante. Para obter etapas, consulte [Guia de Instalação > Habilitar ou desabilitar o modo de manutenção](/docs/commerce-operations/installation-guide/tutorials/maintenance-mode.html#enable-or-disable-maintenance-mode-1) em nosso Guia de Instalação. Adicione seu IP à lista de endereços IP isentos para garantir que você ainda possa acessar seu site para solucionar problemas. Para obter as etapas, consulte [Manter a lista de endereços IP isentos](/docs/commerce-operations/installation-guide/tutorials/maintenance-mode.html#maintain-the-list-of-exempt-ip-addresses) em nosso Guia de Instalação.

**<u>Não!</u>**

* Inicie campanhas de marketing adicionais que podem trazer visualizações de página adicionais para o site.
* Execute indexadores ou crons adicionais que possam causar tensão adicional na CPU ou no disco.
* Execute qualquer tarefa administrativa importante (ou seja, uma ação importante no Administrador do Commerce, como importações/exportações de dados, mídia de limpeza, categorias de salvamento com um grande número de produtos atribuídos e atualizações em massa).
* Limpe o cache.

## Solução

Siga estas etapas para identificar e solucionar problemas da causa.

**Como este é um alerta crítico, é altamente recomendável concluir a Etapa 1 antes de tentar solucionar o problema (Etapa 2 em diante).**

1. Verifique se existe um tíquete de suporte do Adobe Commerce. Para ver as etapas, consulte [Rastrear seus tíquetes de suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#track-tickets) em nossa knowledge base de suporte. O suporte pode já ter recebido um alerta de limite do New Relic, criado um tíquete e começado a trabalhar no problema. Se não houver nenhum ticket, crie um. O ticket deve ter as seguintes informações:

   * Motivo do contato: selecione &quot;Alerta CRÍTICO New Relic recebido&quot;.
   * Descrição do alerta.
   * [Link do incidente do New Relic](https://docs.newrelic.com/docs/alerts-applied-intelligence/new-relic-alerts/alert-incidents/view-violation-event-details-incidents/). Isso está incluído em seus [Alertas Gerenciados do Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md).

1. Se não houver um tíquete de suporte, verifique se a Memória Usada do Redis está aumentando ou diminuindo na página [one.newrelic.com](https://login.newrelic.com) > **Infraestrutura** > **Serviços de terceiros**. Selecione o painel Redis. Se estiver estável ou aumentando, [envie um tíquete de suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) para fazer o upsizing do cluster ou aumente o limite de `maxmemory` para o próximo nível.
1. Se não conseguir identificar a causa do aumento do consumo de memória Redis, analise as tendências recentes para identificar problemas com implantações de código recentes ou alterações de configuração (por exemplo, novos grupos de clientes e grandes alterações no catálogo). É recomendável que você verifique os últimos sete dias de atividade para obter correlações em implantações ou alterações de código.
1. Verifique se há extensões de terceiros que se comportam mal:

   * Tente encontrar uma correlação com extensões de terceiros instaladas recentemente e a hora em que o problema começou.
   * Revise as extensões que poderiam afetar o cache do Adobe Commerce e fazer com que o cache cresça rapidamente. Por exemplo, blocos de layout personalizados, substituição da funcionalidade de cache e armazenamento de grandes quantidades de dados em cache.

1. Se não houver evidência de extensões com comportamento incorreto, [Instale os patches mais recentes para corrigir problemas de Redis para o Adobe Commerce na infraestrutura de nuvem](/help/troubleshooting/miscellaneous/install-latest-patches-to-fix-magento-redis-issues.md).
1. Se as etapas acima não ajudarem a identificar ou solucionar o problema, considere ativar o cache L2 para reduzir o tráfego de rede entre o aplicativo e o Redis. Para obter informações gerais sobre o que é cache L2, consulte [cache L2 no aplicativo do Adobe Commerce](/docs/commerce-operations/configuration-guide/cache/level-two-cache.html) em nossa documentação para desenvolvedores. Para habilitar o cache L2 para a infraestrutura em nuvem, tente o seguinte:

   * Atualize as Ferramentas ECE se estiverem abaixo da versão 2002.1.2.
   * Configure o Cache L2 usando a [variável REDIS\_BACKEND](/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_backend) e atualizando o arquivo `.magento.env.yaml`:

   ```yaml
   stage:
       deploy:
           REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
   ```
