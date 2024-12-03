---
title: Solucionar problemas de desempenho usando o New Relic no Adobe Commerce
description: 'Este artigo fornece etapas de solução de problemas para resolver problemas de desempenho de infraestrutura em nuvem do Adobe Commerce usando o New Relic. Também fornece recursos para obter mais informações. Esta é uma lista de problemas. Clique para ver as etapas de solução de problemas em nossa base de conhecimento de suporte:'
exl-id: 0a22beb7-18b0-47eb-a6b8-63b7322b392c
feature: Observability
role: Developer
source-git-commit: 324cce66df1e4ab7ec4ef8fb6512c3acbabdf3ab
workflow-type: tm+mt
source-wordcount: '900'
ht-degree: 0%

---

# Solucionar problemas de desempenho usando o New Relic no Adobe Commerce

Este artigo fornece etapas de solução de problemas para resolver problemas de desempenho de infraestrutura em nuvem do Adobe Commerce usando o New Relic. Também fornece recursos para obter mais informações. Os seguintes problemas abordados na tabela abaixo com recursos recomendados são:

* Pontuação baixa do Apdex
* Alto uso da CPU
* Operações de E/S altas
* Interrupção

<table>
<tbody>
<tr>
<td>Problema</td>
<td>Solução de problemas</td>
<td>Recursos</td>
</tr>
<tr>
<td>
<p>Baixa pontuação Apdex:</p>
<p>Sua <a href="https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measuring-user-satisfaction">Pontuação do Apdex</a> do New Relic mede a satisfação dos usuários com o tempo de resposta dos seus aplicativos e serviços Web.</p>
</td>
<td>
<p>Você faz logon no <a href="https://login.newrelic.com/login">New Relic</a> &gt; APM &gt; Visão geral. No lado direito da página Visão geral, você verá o gráfico de pontuação do Apdex. Uma pontuação Apdex de 0,5 ou menos é um ponto de preocupação e garante investigação: tempos de transação da Web (solicitações do servidor):</p>
<ol>
<ol>
<li>Faça logon no <a href="https://login.newrelic.com/login">New Relic</a> &gt; APM &gt; (Selecione um aplicativo) &gt; Visão geral. Verifique se o filtro está definido como Tempo de transações da Web no filtro suspenso do gráfico principal. Abaixo na tabela Transactions, procure por App server time. Verifique se você tem transações suspeitas ou de longa duração.</li>
<li>Investigue-as individualmente em Monitoramento &gt; Transações e certifique-se de definir os filtros para Web e Mais demorado<em>.</em>
</li>
<li>Em seguida, pesquise por módulos de terceiros que consomem recursos: provedores de pagamento, ERP etc.</li>
<li>Na seção Monitoramento de APM:<ol>
<li>Clique em Transações.</li>
<li>Role para baixo, clique em Mostrar todas as tabelas de transações.</li>
<li>Você pode classificar transações por <a href="https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems#table_view">vários parâmetros</a> e saltar para aqueles que causam suspeita.</li>
<li>Revise as transações com uma baixa pontuação do Apdex, contagem excepcionalmente alta ou tempo médio alto ou % de dispersão.</li>
<li>Clique em cada transação individual. Se não conseguir resolver o problema, <a href="/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket">envie um tíquete de suporte.</a>
</li>
<li>Se precisar investigar mais, considere verificar transações que não sejam da Web.</li>
</ol>
</li>
</ol>
</ol>
<p>Horário de transação não-Web (operações e tarefas em segundo plano):</p>
<ol>
<ol>
<li>Faça logon no <a href="https://login.newrelic.com/login">New Relic</a> &gt; APM &gt; (Selecione um aplicativo) &gt; Visão geral. Selecione o tempo das transações que não são da Web no filtro suspenso do gráfico principal. Clique em transações individuais na tabela Transações. Procure transações suspeitas ou de longa duração. Isso inclui trabalhos de back-end, trabalhos cron ou trabalhos de importação/exportação, incluindo trabalhos de terceiros.</li>
</ol>
</ol>
</td>
<td>
<p>Para saber mais sobre a pontuação do Apdex do New Relic, consulte <a href="https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction">Documentação do New Relic &gt; Apdex APM &gt; Medir a satisfação do usuário</a>. Você também pode consultar <a href="/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce-apdex-warning-alert.md">Alertas gerenciados para Adobe Commerce: alerta de aviso Apdex</a> em nossa base de dados de conhecimento de suporte.</p>
</td>
</tr>
<tr>
<td>
<p>Alto uso da CPU:</p>
<p>O alto uso da CPU pode indicar que há um serviço particularmente ocupado, como MySQL, Redis, etc.</p>
</td>
<td>
<ol>
<li>Faça logon no <a href="https://login.newrelic.com/login">New Relic</a> &gt; Infraestrutura &gt; Processos.</li>
<li>Revise os gráficos da CPU para ver se há algum processo paralisado ou de alto consumo que esteja usando mais de 100% do tempo da CPU e compare com a contagem do processador na instância. Preste atenção aos picos na utilização de recursos. Não é recomendável matar um processo, a menos que seja um cron travado.</li>
</ol>
</td>
<td>
<p>Para saber mais sobre métricas de desempenho, especialmente porcentagem de CPU, bytes de E/S e uso de memória para processos individuais ou grupos de processos, consulte a <a href="https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#processes">página Documentação do New Relic &gt; Interface de Infraestrutura &gt; página Host de Infraestrutura &gt; guia Processos</a>.</p>
</td>
</tr>
<tr>
<td>
<p>Operações de E/S altas: para cada cliente, esse número seria individual, mas será significativamente diferente da média.</p>
</td>
<td>
<p>Procure um pico incomum em comparação com operações de E/S médias anteriores:</p>
<ol>
<li>Faça logon no <a href="https://login.newrelic.com/login">New Relic</a> &gt; Infraestrutura &gt; Processos.</li>
<li>Revise o gráfico de Bytes de Leitura de E/S por Segundo.</li>
<li>Registre a hora do pico.</li>
<li>Clique em APM.</li>
<li>Selecione o tempo de transações da web no filtro suspenso do gráfico principal.</li>
<li>Defina o tempo para o pico registrado.</li>
<li>Procurar transações que causaram operações de E/S altas.</li>
<li>Aprofunde-se em cada rastreamento de Transação &gt; Detalhes de rastreamento para encontrar o que pode estar causando problemas.</li>
</ol>
</td>
</tr>
<tr>
<td>
<p>Interrupção: o New Relic determina interrupções pela Apdex. Você verá uma linha vermelha no gráfico de pontuação do Apdex, que indica Apdex &lt; 0,4, que é considerado uma interrupção.</p>
</td>
<td>
<p>A investigação de uma interrupção pode tomar várias etapas, examinando transações da Web e não-Web, bancos de dados e transações de terceiros. Transações da Web:</p>
<ol>
<li>Faça logon no <a href="https://login.newrelic.com/login">New Relic</a> &gt; APM &gt; Visão geral. Verifique se o filtro está definido como Tempo de transações da Web no filtro de gráfico suspenso.</li>
<li>Restrinja manualmente a janela de tempo.</li>
<li>Clique em Transações. Verifique se os filtros estão definidos como Web e Mais demorado. Investigue a transação de execução mais longa.</li>
<li>Se precisar investigar mais, considere verificar transações que não sejam da Web.</li>
</ol>
<p>Transações que não são da Web:</p>
<ol>
<li>Retorne à página Visão geral e alterne para Transações que não sejam da Web no filtro suspenso.</li>
<li>Revise os rastreamentos de transação na parte inferior da página, um por um.</li>
<li>Dependendo do problema, você pode precisar usar uma ferramenta de terceiros como um profiler PHP para encontrar um gargalo.</li>
<li>Se precisar investigar mais, considere examinar os processos do banco de dados.</li>
</ol>
<p>Processos de banco de dados:</p>
<ol>
<li>Na página APM, vá para Monitoring &gt; Databases.</li>
<li>Classifique por Mais demorado.</li>
<li>Revise as principais consultas.

Observação: <code>ATUALIZAR</code> ou <code>INSERT</code>as consultas são as consultas que mais consomem CPU.</li>
<li>Alterne para Throughput do seletor Classificar por e procure os processos que causaram a queda do throughput do banco de dados.</li>
<li>Se precisar investigar mais, considere examinar serviços de terceiros.</li>
</ol>
<p>Serviços de terceiros:</p>
<ol>
<li>Na página APM, vá para Monitoring &gt; External services.</li>
<li>Selecione o Tempo médio de resposta mais lento na lista drop-down Classificar por.</li>
<li>Procure processos que ocorreram antes da interrupção.</li>
</ol>
</td>
<td>
<p>Para saber mais sobre como investigar problemas de desempenho específicos, consulte <a href="https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems#tx_functions">Documentação do New Relic &gt; páginas da interface do usuário do APM &gt; página Transações &gt; Usar funções de detalhamento</a>.</p>
</td>
</tr>
</tbody>
</table>
