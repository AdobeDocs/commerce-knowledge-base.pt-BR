---
title: "Alertas gerenciados no Adobe Commerce: alerta de aviso de memória Redis"
description: '"Este artigo fornece etapas de solução de problemas para quando você recebe um alerta de aviso Redis para Adobe Commerce no New Relic. É necessária ação imediata para resolver o problema. O alerta será semelhante ao seguinte, dependendo do canal de notificação de alerta selecionado:'''
exl-id: b7867a42-3817-4cb4-93cf-d69acee33a41
feature: Categories, Marketing Tools, Observability, Services, Support, Tools and External Services, Variables
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '583'
ht-degree: 0%

---

# Alertas gerenciados no Adobe Commerce: alerta de aviso de memória Redis

Este artigo fornece etapas de solução de problemas para quando você recebe um alerta de aviso Redis para Adobe Commerce no New Relic. É necessária ação imediata para resolver o problema. O alerta será semelhante ao seguinte, dependendo do canal de notificação de alerta selecionado:

![new_relic_redis_memory_warning.png](assets/new_relic_redis_memory_warning.png)

## Produtos e versões afetados

Todas as versões da arquitetura do plano Pro da infraestrutura em nuvem do Adobe Commerce.

## Problema

Você receberá um alerta no New Relic se tiver se inscrito no [Alertas gerenciados para o Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md) e um ou mais limites de alerta foram ultrapassados. Esses alertas foram desenvolvidos pela Adobe para fornecer aos comerciantes um conjunto padrão de alertas usando insights do suporte e da engenharia.

**<u>Faça!</u>**

* É recomendável suspender qualquer implantação agendada até que esse alerta seja limpo.
* Se o site estiver respondendo ou ficar totalmente sem resposta, coloque-o imediatamente no modo de manutenção. Para obter etapas, consulte [Guia de instalação > Ativar ou desativar o modo de manutenção](/docs/commerce-operations/installation-guide/tutorials/maintenance-mode.html#enable-or-disable-maintenance-mode-1) em nosso Guia de instalação.
* Adicione seu IP à lista de endereços IP isentos para garantir que você ainda possa acessar seu site para solucionar problemas. Para obter etapas, consulte [Manter a lista de endereços IP isentos](/docs/commerce-operations/installation-guide/tutorials/maintenance-mode.html#maintain-the-list-of-exempt-ip-addresses) em nosso Guia de instalação.

**<u>Não!</u>**

* Inicie campanhas de marketing adicionais que podem trazer visualizações de página adicionais para o site.
* Execute indexadores ou crons adicionais que possam causar tensão adicional na CPU ou no disco.
* Execute qualquer tarefa administrativa importante (ou seja, uma ação importante no Administrador do Commerce, como importações/exportações de dados, mídia de limpeza, categorias de salvamento com um grande número de produtos atribuídos e atualizações em massa).
* Limpe o cache.

## Solução

Siga estas etapas para identificar e solucionar problemas da causa.

1. Verifique se a memória Redis Used está aumentando ou diminuindo em [one.newrelic.com](https://login.newrelic.com/login) > **Infraestrutura** > **Serviços de terceiros** selecione o painel Redis. Se estiver estável ou em crescimento, [enviar um tíquete de suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) para fazer o upsizing do cluster ou aumentar o `maxmemory` limite para o próximo nível.
1. Se não conseguir identificar a causa do aumento do consumo de memória Redis, analise as tendências recentes para identificar problemas com implantações de código recentes ou alterações de configuração (por exemplo, novos grupos de clientes e grandes alterações no catálogo). É recomendável que você verifique os últimos sete dias de atividade para obter correlações em implantações ou alterações de código.
1. Verifique se há extensões de terceiros que se comportam mal:
   * Tente encontrar uma correlação com extensões de terceiros instaladas recentemente e a hora em que o problema começou.
   * Revise as extensões que poderiam afetar o cache do Adobe Commerce e fazer com que o cache cresça rapidamente. Por exemplo, blocos de layout personalizados, substituição da funcionalidade de cache e armazenamento de grandes quantidades de dados em cache.
1. Se não houver indícios de falhas nas extensões, [Instale os patches mais recentes para corrigir problemas do Redis para Adobe Commerce na infraestrutura em nuvem](/help/troubleshooting/miscellaneous/install-latest-patches-to-fix-magento-redis-issues.md). Se as etapas acima não ajudarem a identificar ou solucionar o problema, considere ativar o cache L2 para reduzir o tráfego de rede entre o aplicativo e o Redis. Para obter informações gerais sobre cache L2, consulte [Armazenamento em cache L2 no aplicativo Adobe Commerce](/docs/commerce-operations/configuration-guide/cache/level-two-cache.html) em nosso Guia de configuração. Para habilitar o cache L2 para a infraestrutura em nuvem, tente o seguinte:
   * Atualize as Ferramentas ECE se estiverem abaixo da versão 2002.1.2.
   * Configure o cache L2 usando [Usar variável REDIS\_BACKEND](/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_backend) e atualização `.magento.env.yaml` arquivo:

   ```yaml
   stage:
      deploy:
          REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
   ```
