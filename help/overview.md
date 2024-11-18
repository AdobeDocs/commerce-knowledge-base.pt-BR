---
title: Knowledge base de suporte do Adobe Commerce
description: Tudo o que você precisa saber para solucionar problemas e manter sua loja da Commerce.
exl-id: feacf38f-2803-4170-a64f-5d7c4567432d
feature: Support
role: Admin
source-git-commit: 52d07e5a5bb7be492f6799d0e5ad9fd49c3a61ae
workflow-type: tm+mt
source-wordcount: '1074'
ht-degree: 0%

---

# Knowledge base de suporte do Adobe Commerce

>[!NOTE]
>
>O Guia da Base de conhecimento de suporte da Adobe Commerce será reestruturado em breve, com seu conteúdo sendo movido para outros locais no Adobe Experience League. Enquanto isso, continuaremos a manter e atualizar o conteúdo deste guia.

![Página inicial da Base de Dados de Conhecimento](../help/assets/knowledge-base-home-page-cover.jpg){width="100%"}

As informações nesta Base de Dados de Conhecimento foram criadas como complementares à [Documentação do Desenvolvedor do Adobe Commerce](https://developer.adobe.com/commerce/docs), ao [Guia do Comerciante do Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-admin/user-guides/home.html) e a outras publicações da Adobe Commerce. Ele aborda a solução de problemas e as práticas recomendadas, anúncios de hosts, responde às perguntas frequentes e destaca cenários específicos que não foram mencionados (por qualquer motivo) na documentação oficial.

## O que há nesta Base de Conhecimento?

| CATEGORIA | DESCRIÇÃO |
| --- | --- |
| [Ferramentas de suporte](/help/support-tools/overview.md) | Melhore sua experiência na loja de comércio eletrônico com as diferentes ferramentas de suporte fornecidas pelo Adobe Commerce. Fornecemos práticas recomendadas personalizadas, ferramentas de diagnóstico e monitoramento e as informações mais relevantes sobre seu site. |
| [Avisos](/help/announcements/overview.md) | Obtenha atualizações importantes das equipes do Adobe Commerce. |
| [Solução de problemas](/help/troubleshooting/overview.md) | Obtenha soluções e patches de autoatendimento da equipe de suporte da Adobe Commerce. |
| [Guia do Usuário da Central de Ajuda](/help/help-center-guide/help-center/magento-help-center-user-guide.md) | Saiba como gerenciar seus tíquetes de suporte, conceder acesso compartilhado e navegar na Knowledge base de maneira eficaz. |
| [Como](/help/how-to/overview.md) | Obtenha instruções passo a passo claras da equipe de suporte da Adobe Commerce. |
| [Perguntas frequentes](/help/faq/overview.md) | Encontre perguntas frequentes sobre políticas, estratégias e informações específicas da Adobe Commerce sobre os recursos da Adobe Commerce. |

## Novidades

<table style="width:100%">
  <tr>
    <th style="width:70%">Descrição</th>
    <th style="width:15%">Tipo</th>
    <th style="width:15%">Data</th>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-25234">Transferência de licença devido à reestruturação:</a> este artigo ajudará você a fazer a transição da propriedade de sua conta da Adobe Commerce com facilidade, incluindo todas as etapas essenciais necessárias para manter seus serviços em execução sem interrupções.
    </td>
    <td>Novo artigo </td>
    <td>14 de novembro de 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-25289">Atualizações de segurança disponíveis para o Adobe Commerce (APSB24-90):</a> Em 12 de novembro de 2024, o Adobe lançou uma atualização de segurança para os recursos Adobe Commerce (na nuvem e no local) e Magento Open Source alimentados pelos Serviços da Commerce e implantados como SaaS (Software as a Service). Esta atualização elimina uma vulnerabilidade <a href="https://helpx.adobe.com/security/severity-ratings.html">crítica</a>. 
    </td>
    <td>Novo artigo </td>
    <td>14 de novembro de 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-25231">O proprietário da conta MageID não pode fazer logon nem enviar um tíquete de suporte:</a> Este artigo aborda o problema do Adobe Commerce em que você não consegue fazer logon em sua conta (MageID) em account.magento.com para enviar um tíquete de suporte.
    </td>
    <td>Novo artigo </td>
    <td>14 de novembro de 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-25135">A extensão OOTB do Braintree para Adobe Commerce não é compatível com os campos mais recentes do Visa 3DS:</a> Este artigo explica como cumprir as novas regulamentações do Visa, pois a extensão Braintree pronta para uso da Adobe Commerce não é compatível com os campos mais recentes do Visa 3DS.
    </td>
    <td>Novo artigo </td>
    <td>14 de novembro de 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-53/acsd-61528-retrieving-roles-using-graphql-returns-no-results">ACSD-61528: recuperar funções usando o GraphQL não retorna resultados:</a> O patch ACSD-61528 corrige o problema em que a recuperação de funções do administrador da empresa usando o GraphQL sempre retorna um resultado nulo. Este patch está disponível quando o [!DNL Quality Patches Tool (QPT)] 1.1.53 está instalado.
    </td>
    <td>Novo artigo </td>
    <td>14 de novembro de 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-53/acsd-48318-environment-emulation-nesting-error-in-system-log">ACSD-48318: erro de aninhamento de emulação de ambiente em system.log:</a> O patch ACSD-48318 corrige o problema em que uma mensagem de erro <em>main.ERROR:Aninhamento de emulação de ambiente não é permitido</em> aparece em <code>system.log</code> toda vez que um email de fatura é enviado. Este patch está disponível quando o [!DNL Quality Patches Tool (QPT)] 1.1.53 está instalado.
    </td>
    <td>Novo artigo </td>
    <td>14 de novembro de 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-52/acsd-59366-delete-teams-with-deactivated-users-not-visible-in-the-team-list">ACSD-59366: excluir equipes com usuários desativados não visíveis na lista de equipes:</a> O patch ACSD-59366 corrige o problema em que ocorre um erro ao tentar excluir uma equipe que contém usuários desativados que não estão visíveis na lista de equipes. Este patch está disponível quando o [!DNL Quality Patches Tool (QPT)] 1.1.52 está instalado.
    </td>
    <td>Novo artigo </td>
    <td>14 de novembro de 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-51/acsd-60234-paypal-shows-an-incorrect-amount-when-discount-is-applied">ACSD-60234: o PayPal mostra um valor incorreto quando o desconto é aplicado:</a> O patch ACSD-60234 corrige o problema em que [!DNL PayPal] mostra um valor incorreto quando o desconto é aplicado por meio do método de pagamento. Este patch está disponível quando o [!DNL Quality Patches Tool (QPT)] 1.1.51 está instalado.
    </td>
    <td>Novo artigo </td>
    <td>14 de novembro de 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-52/acsd-60673-cart-price-rule-fix-for-multiple-payment-methods-at-checkout">ACSD-60673: problema de Regra de Preço do Carrinho corrigido para vários métodos de pagamento no check-out:</a> O patch ACSD-60673 corrige o problema em que os descontos de um [!UICONTROL Cart Price Rule] que usa uma condição de método de pagamento nem sempre são listados nos totais. Este patch está disponível quando o [!DNL Quality Patches Tool (QPT)] 1.1.52 está instalado.
    </td>
    <td>Novo artigo </td>
    <td>14 de novembro de 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-53/acsd-60584-access-token-created-for-one-website-is-allowed-to-access-information-on-other-websites">ACSD-60584: O token de acesso criado para um site tem permissão para acessar informações em outros sites:</a> O patch ACSD-60584 corrige o problema em que o token de acesso criado para o usuário em um site tem permissão para acessar ou alterar informações do cliente em outros sites. Este patch está disponível quando o [!DNL Quality Patches Tool (QPT)] 1.1.53 está instalado.
    </td>
    <td>Novo artigo </td>
    <td>14 de novembro de 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-52/acsd-60788-fixes-issue-where-custom-scripts-for-google-tag-manager-are-not-executed-due-to-content-security-policy-errors">ACSD-60788: scripts personalizados para o Gerenciador de Marcas do Google não são executados devido a erros de Política de Segurança de Conteúdo:</a> O patch ACSD-60788 corrige o problema em que scripts personalizados para [!DNL Google Tag Manager] não são executados devido a erros de Política de Segurança de Conteúdo. Este patch está disponível quando o [!DNL Quality Patches Tool (QPT)] 1.1.52 está instalado.
    </td>
    <td>Novo artigo </td>
    <td>14 de novembro de 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-52/acsd-61366-setup-command-fails-with-error">ACSD-61366: O comando <code>bin/magento setup:static-content:deploy --jobs 4</code> encontra várias falhas de trabalho com um erro:</a> O patch ACSD-61366 corrige o problema em que o comando <code>bin/magento setup:static-content:deploy --jobs 4</code> encontra várias falhas de trabalho com o erro <em>A porta deve ser configurada dentro do parâmetro de host</em>, apesar de especificar a porta para a conexão DB. Este patch está disponível quando o [!DNL Quality Patches Tool (QPT)] 1.1.52 está instalado.
    </td>
    <td>Novo artigo </td>
    <td>14 de novembro de 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-51/acsd-60816-newrelic-browser-monitoring-scripts-injected-by-apm-agent-are-not-compliant-with-csp">ACSD-60816: os scripts de monitoramento de navegador New Relic inseridos pelo agente APM não são compatíveis com o CSP:</a> O patch ACSD-60816 corrige o problema em que os [!DNL New Relic] scripts de monitoramento de navegador inseridos pelo agente APM não são compatíveis com a Política de Segurança de Conteúdo (CSP). Este patch está disponível quando o [!DNL Quality Patches Tool (QPT)] 1.1.51 está instalado.
    </td>
    <td>Novo artigo </td>
    <td>14 de novembro de 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-52/acsd-59952-error-on-deleting-shared-catalog-with-same-group-id-as-another-shared-catalog">ACSD-59952: Erro ao excluir catálogo compartilhado com a mesma ID de grupo de outro catálogo compartilhado:</a> O patch ACSD-59952 corrige o erro lançado ao excluir catálogos compartilhados com o mesmo <code>customer_group_id</code> como outro catálogo compartilhado. Isso impede ainda mais que os usuários criem esses catálogos compartilhados. Este patch está disponível quando o [!DNL Quality Patches Tool (QPT)] 1.1.52 está instalado.
    </td>
    <td>Novo artigo </td>
    <td>14 de novembro de 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-51/acsd-59786-graphql-returns-an-error-when-fetching-a-quote-id-for-an-expired-quote">ACSD-59786: o GraphQL retorna um erro ao buscar um <code>quote_id</code> para uma cotação expirada:</a> O patch ACSD-59786 corrige o problema em que uma consulta do GraphQL retorna um erro ao buscar um <code>quote_id</code> para uma cotação expirada. Este patch está disponível quando o [!DNL Quality Patches Tool (QPT)] 1.1.51 está instalado.
    </td>
    <td>Novo artigo </td>
    <td>14 de novembro de 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-51/acsd-59967-javascript-error-prevents-google-maps-from-rendering-correctly">ACSD-59967: o erro do JavaScript impede que o Google Maps seja renderizado corretamente:</a> O patch ACSD-59967 corrige o problema em que o erro do JavaScript impede que o [!DNL Google Maps] seja renderizado corretamente. Este patch está disponível quando o [!DNL Quality Patches Tool (QPT)] 1.1.51 está instalado.
    </td>
    <td>Novo artigo </td>
    <td>14 de novembro de 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-53/acsd-59930-improves-performance-of-company-flows">ACSD-59930: melhora o desempenho dos fluxos da empresa:</a> O patch ACSD-59930 corrige o problema em que um erro <em>Tempo limite</em> é exibido no painel de administração ao criar, salvar ou excluir uma empresa com um administrador que tenha mais de 1000 endereços no catálogo de endereços. Este patch está disponível quando o [!DNL Quality Patches Tool (QPT)] 1.1.53 está instalado.
    </td>
    <td>Novo artigo </td>
    <td>14 de novembro de 2024</td>
  </tr>
</table>
