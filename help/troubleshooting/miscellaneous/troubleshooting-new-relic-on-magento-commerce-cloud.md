---
title: Solução de problemas do New Relic no Adobe Commerce na infraestrutura em nuvem
description: Este artigo fornece recursos para solução de problemas do New Relic no Adobe Commerce na infraestrutura em nuvem.
exl-id: ea763291-5c9b-4575-b2ee-820dbc367743
feature: Cloud, Observability, Paas
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 0%

---

# Solução de problemas do New Relic no Adobe Commerce na infraestrutura em nuvem

Este artigo fornece recursos para solução de problemas do New Relic no Adobe Commerce na infraestrutura em nuvem.

<table>
<tbody>
<tr>
<td class="wysiwyg-text-align-center"><strong>Problema</strong></td>
<td class="wysiwyg-text-align-center"><strong>Causa</strong></td>
<td class="wysiwyg-text-align-center"><strong>Recursos</strong></td>
</tr>
<tr>
<td class="wysiwyg-text-align-center" colspan="3">Problemas de acesso</td>
</tr>
<tr>
<td>
<p><u>Não é possível visualizar projetos no New Relic.</u></p>
<p>Você faz logon no <em>New Relic</em>, mas não pode ver os projetos que você deveria ter direito a visualizar/acessar.</p>
</td>
<td>
<p>Nesses casos, um usuário administrador precisa adicioná-lo ao projeto.</p>
</td>
<td>
<p><a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/faq/access-new-relic-services.html">Acessando os serviços da New Relic</a> em nossa base de dados de conhecimento de suporte.</p>
</td>
</tr>
<tr>
<td class="wysiwyg-text-align-center" colspan="3">Problemas de dados</td>
</tr>
<tr>
<td>
<p><u>Dados ausentes após a instalação.</u></p>
<p>Use o <a href="https://docs.newrelic.com/docs/agents/manage-apm-agents/troubleshooting/new-relic-diagnostics">utilitário New Relic Diagnostics</a> para tentar identificar a causa. Se isso não ajudar, analise as soluções específicas do agente. Os links para artigos que contêm essas soluções estão na coluna à direita.</p>
</td>
<td>
<p>A ausência de dados pode ter causas diferentes. Talvez seja necessário:</p>
<ul>
<li>Verifique se o agente está instalado.</li>
<li>Verifique o nome do aplicativo e a chave de licença.</li>
<li>Reinicie o servidor Web.</li>
<li>Verifique se o seu sistema atende aos requisitos de compatibilidade.</li>
<li>Configurações de INI.</li>
</ul>
</td>
<td>
<ul>
<li><a href="https://docs.newrelic.com/docs/agents/manage-apm-agents/troubleshooting/not-seeing-data#apm-agents">Documentação do New Relic &gt; Agentes APM &gt; Dados não visualizados</a></li>
<li><a href="https://docs.newrelic.com/docs/agents/manage-apm-agents/troubleshooting/not-seeing-data#browser-agent">Documentação do New Relic &gt; Navegador New Relic &gt; Dados não visualizados</a></li>
<li><a href="https://docs.newrelic.com/docs/agents/manage-apm-agents/troubleshooting/not-seeing-data#infrastructure-agents">Documentação do New Relic &gt; Infraestrutura New Relic &gt; Não visualização de dados</a></li>
<li><a href="https://docs.newrelic.com/docs/agents/manage-apm-agents/troubleshooting/not-seeing-data#mobile-agents">Documentação do New Relic &gt; New Relic Mobile &gt; Dados não visualizados</a></li>
</ul>
</td>
</tr>
<tr>
<td>
<p><u>Discrepância do carimbo de data/hora das transações.</u> Talvez você tenha dificuldades para encontrar transações longas (mais de 5 minutos) usando a interface do usuário do New Relic. Você também pode encontrar transações exibidas fora do intervalo de tempo esperado.</p>
</td>
<td>
<p>A interface do usuário do New Relic exibe a hora do fim da transação, não a hora em que a transação começou.</p>
</td>
<td>
<p>Para calcular o início da transação usando a interface do usuário do New Relic, verifique a duração da transação. Subtraia a quantidade de duração do carimbo de data e hora (fim da transação) fornecido pela interface do usuário do New Relic.</p>
</td>
</tr>
<tr>
<td>
<p>As consultas <u>NerdGraph GraphQL <code>curl</code> usando caracteres especiais como <code>|</code> e <code>%</code> não funcionam</u>.</p>
</td>
<td>
<p>Atualmente, o recurso "copiar para curl" do New Relic no NerdGraph não fornece uma maneira de lidar com caracteres especiais como <code>|</code> e <code>%</code>.</p>
</td>
<td>
<p>Use uma biblioteca de API diferente para resolver o problema com caracteres especiais. Por exemplo, Biblioteca GraphQLClient para API Graphql no Python ou Apache.commons por chamadas de linguagem Java. Revise as bibliotecas de clientes no <a href="https://graphql.org/code/">GraphQL</a>.</p>
</td>
</tr>
<tr>
<td>
<p><u>Problemas de exibição de gráfico e painel.</u></p>
</td>
<td>
<p>Resolva os gráficos ausentes adicionando domínios do New Relic à lista de permissões ou desinstale a extensão do navegador que está causando os problemas.</p>
</td>
<td>
<p><a href="https://docs.newrelic.com/docs/apm/new-relic-apm/troubleshooting/charts-missing-or-do-not-render">Documentação do New Relic &gt; Gráficos ausentes ou não renderizados</a> </p>
</td>
</tr>
<tr>
<td class="wysiwyg-text-align-center" colspan="3">Problemas do agente PHP</td>
</tr>
<tr>
<td>
<p><u>O agente do PHP não mostra a contagem de instâncias correta.</u></p>
</td>
<td>
<p>O número de instâncias pode aumentar dependendo dos processos de back-end e da taxa de transferência. As diferenças entre valores de servidor podem ocorrer devido a processos executados em um servidor, mas não no outro.</p>
</td>
<td>
<p><a href="https://docs.newrelic.com/docs/agents/php-agent/troubleshooting/troubleshoot-php-agent-instance-count">Documentação do New Relic &gt; Solucionar problemas da contagem de instâncias do agente PHP</a> </p>
</td>
</tr>
</tbody>
</table>
