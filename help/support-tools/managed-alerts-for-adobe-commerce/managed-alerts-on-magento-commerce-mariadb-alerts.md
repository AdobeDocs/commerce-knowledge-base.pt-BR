---
title: "Alertas gerenciados no Adobe Commerce: alertas do MariaDB"
description: '"Este artigo fornece etapas de solução de problemas quando você recebe alertas MariaDB para Adobe Commerce no New Relic. Os alertas do MariaDB monitoram a alta carga de consultas, bem como o excesso de consultas DML (Data Manipulation Language). Ambos podem levar a uma experiência degradada do usuário ou até mesmo a um tempo de inatividade. Você pode receber quatro tipos de alertas:'''
exl-id: 707e20e0-faba-4bcd-884c-b54568787442
feature: Cache, Observability, Support, Tools and External Services
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '583'
ht-degree: 0%

---

# Alertas gerenciados no Adobe Commerce: alertas do MariaDB

Este artigo fornece etapas de solução de problemas quando você recebe alertas MariaDB para Adobe Commerce no New Relic. Os alertas do MariaDB monitoram a alta carga de consultas, bem como o excesso de consultas DML (Data Manipulation Language). Ambos podem levar a uma experiência degradada do usuário ou até mesmo a um tempo de inatividade. Você pode receber quatro tipos de alertas:

* Aviso de Consultas DML
* Consultas DML Críticas

## **Produtos e versões afetados**

Arquitetura do plano Pro da infraestrutura em nuvem do Adobe Commerce

## Problema

Você receberá um alerta gerenciado no New Relic se tiver se inscrito no [Alertas gerenciados para o Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md) e um ou mais limites de alerta foram ultrapassados. Esses alertas foram desenvolvidos pela Adobe para fornecer aos clientes um conjunto padrão usando insights do suporte e da engenharia.

**Faça!**

* Anule qualquer implantação programada até que esse alerta seja limpo.
* Coloque o site no modo de manutenção imediatamente se ele estiver ou se tornar totalmente inoperante. Para etapas, consulte [Guia de instalação > Ativar ou desativar o modo de manutenção](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten) na documentação do desenvolvedor. Adicione seu IP à lista de endereços IP isentos para garantir que você ainda possa acessar seu site para solucionar problemas. Para obter etapas, consulte [Manter a lista de endereços IP isentos](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten#instgde-cli-maint-exempt).
* Encerre todos os scripts, como importações, que podem ser a causa do alerta se o desempenho do site for afetado.

**Não!**

* Execute indexadores ou crons adicionais que podem causar stress adicional no MariaDB.
* Execute qualquer tarefa administrativa importante (ou seja, Commerce Admin, importações/exportações de dados).
* Limpe o cache.

## Solução

**Consultas DML (consultas que modificam o banco de dados usando UPDATE, INSERT e DELETE)**

Se você receber um alerta Crítico de Consultas DML, comece na primeira etapa. Se você receber um alerta de Aviso de Consultas DML, comece na etapa dois.

1. Verifique se existe um tíquete de suporte do Adobe Commerce. Para obter as etapas, consulte nossa base de conhecimento [Acompanhe seus tíquetes de suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#track-tickets). O suporte do pode ter recebido um alerta de limite do New Relic, criado um tíquete e começado a trabalhar no problema. Se não houver nenhum ticket, crie um. O ticket deve ter as seguintes informações:
1. Motivo do contato: selecione &quot;Alerta New Relic MariaDB recebido&quot;.
1. Descrição do alerta.
1. [Link Incidente New Relic](https://docs.newrelic.com/docs/alerts-applied-intelligence/new-relic-alerts/alert-incidents/view-violation-event-details-incidents). Isso está incluído no seu [Alertas gerenciados para o Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md).
1. Para identificar a origem do problema, tente identificar as consultas DML:
1. Revisar as operações do banco de dados usando etapas do New Relic [Páginas de Interface do Usuário APM > Monitoramento > página Bancos de Dados](https://docs.newrelic.com/docs/apm/apm-ui-pages/monitoring/databases-page-view-operations-throughput-response-time) .
1. Classifique por CONTAGEM DE CHAMADAS, OPERAÇÃO. Revise as operações INSERT, DELETE e UPDATE.
1. Procure por AVG alta.
1. Clique em para localizar chamadores de operação de banco de dados. Isso identificará as transações usando essa consulta por tempo.
1. Procure otimizações de código ou otimizações operacionais:
1. Otimizações de código: procure otimizar consultas com inserções/atualizações em massa, minimizando o uso de índice ou limitando o código.
1. Otimizações operacionais: descarregamento de modificações de dados que consomem muitos recursos para diminuir os tempos de tráfego.
1. Otimizações adicionais: certifique-se de que você está na versão mais recente de ECE-Tools. Para obter etapas, consulte [Nuvem para Adobe Commerce > Atualizar versão das ferramentas ece](https://devdocs.magento.com/cloud/project/ece-tools-update.html) na documentação do desenvolvedor.

## Leitura relacionada

* Para pesquisar outros problemas comuns do MariaDB, consulte [Problemas mais comuns de banco de dados do Adobe Commerce na infraestrutura em nuvem](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/resolve-database-performance-issues.html).
* Para pesquisar as práticas recomendadas do banco de dados, consulte [Práticas recomendadas de banco de dados para o Adobe Commerce na infraestrutura em nuvem](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html).
