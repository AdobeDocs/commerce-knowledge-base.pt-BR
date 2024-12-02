---
title: 'Firewall para aplicativos Web (WAF) ativado por Fastly: the FAQ'
description: Os firewalls de aplicações Web (WAFs) impedem que tráfego mal-intencionado entre em sites e redes ao filtrar o tráfego em relação a um conjunto de regras de segurança. O tráfego que aciona qualquer uma das regras é bloqueado antes que possa danificar seus sites ou a rede.
exl-id: d977ea68-7d8c-4863-b026-acdc25d8c430
feature: Cache
source-git-commit: f384ff9d5d8a8c5c5da20b582c02a2d783b32d7e
workflow-type: tm+mt
source-wordcount: '1654'
ht-degree: 0%

---

# Firewall para aplicativos Web (WAF) ativado por Fastly: the FAQ

## Como funciona o Adobe Commerce Managed Cloud WAF (viabilizado pelo Fastly)?

Os firewalls de aplicativos Web (WAFs) impedem que [tráfego mal-intencionado](/help/how-to/general/block-malicious-traffic-for-magento-commerce-on-fastly-level.md) entre em sites e redes ao filtrar o tráfego em relação a um conjunto de regras de segurança. O tráfego que aciona qualquer uma das regras é bloqueado antes que possa danificar seus sites ou a rede.

O Adobe Commerce Cloud WAF fornece uma política do WAF com um conjunto de regras projetado para proteger seus aplicativos Web do Adobe Commerce contra uma grande variedade de ataques.

O WAF examina o tráfego da Web e do administrador para identificar qualquer atividade suspeita. Ele avalia o GET e o tráfego de POST (chamadas de API HTTP) e aplica o conjunto de regras para determinar qual tráfego bloquear. O WAF pode bloquear uma grande variedade de ataques, incluindo ataques de injeção de SQL, ataques de script entre sites, ataques de exfiltração de dados e violações de protocolo HTTP.

Como um serviço baseado em nuvem, a WAF não requer hardware ou software para instalar ou manter. O Fastly, um parceiro de tecnologia existente, fornece o software e a experiência. O WAF de alto desempenho e sempre ativo reside em cada nó de cache da rede de fornecimento global da Fastly.

## O WAF está disponível para todos os clientes de nuvem?

Sim, o serviço de nuvem do WAF está incluído em sua assinatura do Adobe Commerce na infraestrutura em nuvem para os planos de arquitetura do plano inicial do Adobe Commerce na infraestrutura em nuvem e de arquitetura do plano Pro do Adobe Commerce na infraestrutura em nuvem sem custo adicional. O serviço WAF está disponível em ambientes de produção e de preparo.

## O WAF atende aos requisitos do PCI DSS 6.6?

Sim.

## Se minha conta do Adobe Commerce na infraestrutura em nuvem gerencia sites em vários domínios, o perfil do WAF é ajustado para cada domínio ou coletivamente para todos os domínios?

O WAF é ajustado coletivamente para todos os domínios em uma única conta de nuvem.

## Quais regras são usadas para a WAF?

O conjunto de regras no perfil do WAF aplicado ao seu ambiente de produção do Adobe Commerce na infraestrutura em nuvem baseia-se no conjunto de regras dos 10 principais recursos de proteção contra ameaças do OWASP, que abrange explorações comuns em serviços da Web. Ele também contém regras específicas do Adobe Commerce desenvolvidas pela TrustWave SpiderLabs. A equipe de Pesquisa de segurança da Fastly adicionou regras que protegem seu site e sua rede contra ataques conhecidos: endereços IP inválidos, agentes de usuário inválidos e nós de controle e comando botnet conhecidos. Ativamos regras no OWASP Paranoia Nível 3 ou inferior, o que fornece cobertura de alta segurança.

## Como faço para acessar os logs?

Para enviar os logs para sua ferramenta de registro, trabalhe com seu gerente técnico de conta (TAM) para adicionar um terminal de registro no Fastly.

## Como é uma solicitação de bloqueio?

Uma solicitação bloqueada retorna uma página 403 com um identificador de solicitação.

Você pode personalizar essa página, desde que a personalização inclua o identificador da solicitação. Entre em contato com seu gerente técnico de conta para obter detalhes.

## Como atualizamos os conjuntos de regras do WAF? Com que rapidez uma regra do WAF pode ser alterada ou atualizada e aplicada globalmente na produção?

Como parte do serviço do Cloud WAF, o Fastly gerencia atualizações de regras de terceiros comerciais, pesquisas do Fastly e fontes abertas. Eles atualizam as regras publicadas em uma política conforme necessário ou quando alterações nas regras estão disponíveis em suas respectivas fontes. Novas regras que correspondem às classes de regras publicadas também são inseridas na instância do WAF de qualquer serviço depois que ele é ativado. Isso ajuda a garantir a cobertura imediata para explorações novas ou em evolução. Você pode examinar informações [sobre atualizações e manutenção de regras](https://docs.fastly.com/guides/web-application-firewall/fastly-waf-rule-set-updates-maintenance#rule-set-maintenance) no site de documentação do Fastly.

## Qual a diferença entre o Adobe Commerce Cloud WAF e a solução da WAF que o Fastly oferece aos seus clientes diretos?

A solução da WAF vendida diretamente pela Fastly é uma oferta paga que inclui conjuntos de regras mais amplos e recursos adicionais, como personalização de regras e proteção contra malware. A solução de nuvem do WAF da Adobe Commerce inclui um subconjunto de regras direcionadas ao aplicativo Adobe Commerce e inclui apenas um conjunto de regras para cada ambiente de produção do cliente.

## Contra quais tipos de ameaças de segurança a WAF oferece proteção?

<table class="table-basic" style="width: 649px;">
<tbody>
<tr>
<th style="width: 145.5px; text-align: left;">Ameaça</th>
<th style="width: 497.5px; text-align: left;">Proteção do WAF</th>
</tr>
<tr>
<td style="width: 145.5px; vertical-align: top;">Ataques de injeção de SQL</td>
<td style="width: 497.5px;">Tanto o Conjunto de Regras Principais OWASP ModSecurity quanto o Conjunto de Regras Comerciais TrustWave incluem filtros específicos para ataques de injeção de SQL e suas variantes.</td>
</tr>
<tr>
<td style="width: 145.5px; vertical-align: top;">
<p>Injeção entre locais</p>
</td>
<td style="width: 497.5px;">O conjunto de regras do OWASP protege contra ataques de injeção entre sites. O Fastly aproveita um mecanismo de pontuação para cada solicitação que procura por injeção entre sites e outras ameaças à origem. Pontuamos cada solicitação em relação a todo o conjunto de regras principais e validamos se a pontuação da solicitação está abaixo de um limite configurável para que seja aprovada.</td>
</tr>
<tr>
<td style="width: 145.5px; vertical-align: top;">Ataques de força bruta</td>
<td style="width: 497.5px;">Abrangido pelo conjunto de regras do OWASP. O Fastly também bloqueia a atividade de força bruta usando o código VCL, que reconhece fontes específicas, solicitações ou tentativas de força bruta ou sobrecarrega os controles de segurança antes de qualquer tráfego chegar ao data center de origem.</td>
</tr>
<tr>
<td style="width: 145.5px; vertical-align: top;">Ataques de rede</td>
<td style="width: 497.5px;">Os ataques à rede, ou ataques a infraestruturas de rede, são gerenciados automaticamente pelo Fastly. O Fastly não transmite o DNS para a origem, e o tráfego que não corresponde a um perfil HTTP, HTTPS ou DNS estreito é descartado na borda da rede. Ataques direcionados a protocolos de controle são defendidos por meio da autenticação de endpoints em toda a rede. Além disso, os protocolos de rede usados na rede Fastly são reforçados para garantir que não possam ser aproveitados como meio de amplificação ou reflexão. Os clientes são responsáveis por proteger contra ataques que ignoram a rede do Fastly aproveitando o espaço de endereço IP do Fastly Cache, publicado para nossos clientes como um componente do serviço de CDN. Recomenda-se que o espaço de endereço IP de origem não seja publicado no DNS público para garantir que ataques de bypass não possam usar esses endereços como destinos.</td>
</tr>
<tr>
<td style="width: 145.5px; vertical-align: top;">Ataques de injeção de JavaScript</td>
<td style="width: 497.5px;">As regras do WAF protegem contra a inserção de código JavaScript mal-intencionado nas comunicações do cliente com os serviços da Web. Padrões ou pontuações comuns de exploração são filtrados pelo WAF para garantir a integridade do serviço de origem.</td>
</tr>
</tbody>
</table>

## Recursos e funcionalidades adicionais são oferecidos?

A oferta WAF da Adobe Commerce inclui proteção contra as 10 principais ameaças da OWASP como parte dos requisitos do PCI, suporte 24 horas por dia, 7 dias por semana, incluindo triagem para falsos positivos e atualizações de versão. Os seguintes recursos não são compatíveis com a oferta padrão:

* limitação de taxa
* personalizações de regras
* mitigação de bot
* proteção contra malware

## Como o desempenho do meu site é afetado pela WAF?

Uma latência estimada de 1,5 milissegundos (ms) a 20 ms é introduzida a cada solicitação não armazenada em cache.

## Os clientes podem criar e modificar listas negras de IP para bloquear o tráfego?

Sim, os clientes podem habilitar o bloqueio por país e a ACL (lista de controle de acesso) na interface do administrador do Adobe Commerce na infraestrutura em nuvem. Use esses recursos nos casos em que deseja bloquear o acesso de visitantes provenientes de países específicos ou de determinados IPs ou intervalos de IPs. Se você quiser que os visitantes bloqueados vejam uma página personalizada em vez de um código de erro, é possível criar uma página de erro personalizada carregando o HTML no menu de Configuração do Fastly. Consulte [Criar uma página de erro/manutenção personalizada](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html) na documentação do desenvolvedor.

## Onde posso verificar o status operacional do meu serviço da WAF?

A disponibilidade geral do serviço WAF é relatada na [página Status rápido](https://status.fastly.com/). Não são fornecidos relatórios de disponibilidade para o WAF de clientes individuais.

## A Adobe Commerce fornece o Gerenciamento de incidentes para o serviço da WAF?

No momento, o Gerenciamento de incidentes não é oferecido.

## O Adobe Commerce possui um Centro de Operações de Segurança?

Embora a Adobe Commerce não tenha um Centro de Operações de Segurança, temos um processo de operações de segurança que nos permite envolver os recursos certos para responder a incidentes de segurança em tempo real. Também oferecemos suporte 24 horas por dia, 7 dias por semana, 365 dias por ano, após o horário normal.

Você também pode obter notícias e atualizações de segurança relacionadas ao Adobe Commerce na [Central de Segurança](https://helpx.adobe.com/security.html).

## Que suporte está disponível?

O Suporte da WAF oferece os seguintes recursos para ajudá-lo a minimizar os impactos de serviços de solicitações indesejadas ou mal-intencionadas:

* Integração: ativação, configuração inicial e monitoramento limitado do(s) serviço(s) Fastly que oferecem suporte ao Adobe Commerce managed cloud WAF
* Triagem contínua de falso positivo para abordar instâncias em que o WAF bloqueia o tráfego legítimo
* Configuração de quaisquer novas regras padrão introduzidas como parte das atualizações de versão do WAF

Consulte os termos do [Cloud SLA](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Magento-Support-Services-Terms-and-Conditions.pdf) para obter informações adicionais de suporte, incluindo definições de gravidade, tempos de resposta, canais e disponibilidade.

## Se o WAF estiver bloqueando o tráfego legítimo ou causando outros problemas, como posso obter ajuda?

[Enviar um tíquete de suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) na [Central de Ajuda da Adobe Commerce](https://support.magento.com). Inclua, indique que o ticket está relacionado ao serviço do WAF e inclua o identificador (ID) de solicitação bloqueada.

O sistema de emissão de tíquetes de suporte da Adobe Commerce rastreia a comunicação entre nossos engenheiros de suporte e a equipe de um cliente. Esse sistema fornece uma transcrição das comunicações com carimbo de data e hora e envia emails para o cliente e para a equipe da Adobe Commerce à medida que os tíquetes são atualizados.

Para todos os Incidentes enviados online, o recebimento do Incidente será confirmado através do sistema de emissão de tíquetes da Central de Ajuda ao Cliente da Adobe Commerce. Após o recebimento de um incidente devidamente enviado, os serviços de suporte serão priorizados de acordo com os níveis de prioridade estabelecidos acima.

A tabela a seguir resume os canais de suporte e a disponibilidade do Suporte da WAF:

<table class="table-basic">
<tbody>
<tr>
<th>Oferta de suporte</th>
<th>Detalhes</th>
</tr>
<tr>
<td>Ajuda de autoatendimento online</td>
<td>Acesso ilimitado</td>
</tr>
<tr>
<td>Disponibilidade para relatórios de incidentes</td>
<td>24/7</td>
</tr>
<tr>
<td>Portal da Web</td>
<td>Disponível via Zendesk</td>
</tr>
<tr>
<td>Escalonamento de emergência*</td>
<td>Consulte o artigo <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/adobe-commerce-p1-notification-hotline.html">hotline de notificação P1 da Adobe Commerce</a> para ver os números internacionais e dos EUA.</td>
</tr>
</tbody>
</table>

*\* A linha telefônica de suporte gratuito da Adobe Commerce está reservada somente para Incidentes de Prioridade 1. As chamadas que não têm Prioridade 1 irão retardar a resposta geral aos problemas*

## Como os falsos positivos são triados?

Temos um processo de triagem de falsos positivos (disponível 24 horas por dia, 7 dias por semana) para solucionar rapidamente as instâncias em que solicitações legítimas acionaram uma regra do WAF. Os eventos falsos positivos são tratados como problemas de prioridade 1. Como ação padrão, nossa equipe de suporte pode atualizar a política do WAF imediatamente para desativar a regra que acionou o evento de bloqueio e permitir que a solicitação legítima passe pelo WAF.

## E se o tráfego para a seção de administrador do Adobe Commerce no site da infraestrutura em nuvem acionar as regras do WAF? O Suporte da Adobe Commerce resolverá problemas com o tráfego administrativo bloqueado?

Sim, o tráfego de administrador bloqueado é tratado como um problema de Prioridade 1.
