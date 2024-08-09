---
title: Knowledge base de suporte do Adobe Commerce
description: Tudo o que você precisa saber para solucionar problemas e manter sua loja da Commerce.
exl-id: feacf38f-2803-4170-a64f-5d7c4567432d
feature: Support
role: Admin
source-git-commit: cfbe281941fbdc3e6fe7ee36385dc6732b46da26
workflow-type: tm+mt
source-wordcount: '1395'
ht-degree: 0%

---

# Knowledge base de suporte do Adobe Commerce

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

>[!NOTE]
>
>Para registrar um novo tíquete, entre na [Central de Ajuda da Adobe Commerce](https://support.magento.com/) e siga as etapas detalhadas em [Enviar um Tíquete de Suporte](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#submit-ticket).
>
>Se você não vir a opção de enviar um tíquete, consulte a seção *[Enviar um link de tíquete não exibido](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#no-submit-link)* em nosso [Guia do Usuário da Central de Ajuda](/help/help-center-guide/help-center/magento-help-center-user-guide.md).

## Novidades

<table style="width:100%">
  <tr>
    <th style="width:70%">Descrição</th>
    <th style="width:15%">Tipo</th>
    <th style="width:15%">Data</th>
  </tr>

<tr>
    <td>
    <a href = "https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/the-magento-cloud-cli-doesnt-show-an-active-environment">A CLI do <code>Magento-cloud</code> não mostra um ambiente ativo:</a> Há vários ambientes ativos e você está tentando interagir com um ambiente executando um comando Magento-cloud CLI (ferramenta de linha de comando). No entanto, o prompt para escolher o ambiente desejado não lista esse ambiente.
    </td>
    <td>Novo artigo</td>
    <td>30 de julho de 2024</td>
  </tr>

<td>
    <a href = "https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/how-to-obtain-and-apply-security-patches">Como obter e aplicar um patch de segurança:</a> Este artigo fornece instruções sobre como obter e aplicar um patch de segurança que foi lançado, mas as instruções não estão disponíveis.  
    </td>
    <td>Novo artigo</td>
    <td>30 de julho de 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/elasticsearch/falling-back-to-elasticsearch7-when-search-engine-set-to-opensearch">Falling de volta para Elasticsearch7 quando o mecanismo de pesquisa estiver definido como Opensearch:</a> Este artigo fornece uma solução para o problema quando ocorre um erro Falling de volta para Elasticsearch7 quando o mecanismo de pesquisa está definido como OpenSearch no Adobe Commerce. 
    </td>
    <td>Novo artigo </td>
    <td>30 de julho de 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/deployment/deployment-failed-there-are-no-commands-defined-in-the-cache-namespace-error">Falha na implantação: não há comandos definidos no erro de namespace 'cache':</a> Este artigo fornece uma solução para o problema quando a implantação falha e um dos erros mostrados no log é <em>Não há comandos definidos no namespace "cache"</em>. 
    </td>
    <td>Novo artigo </td>
    <td>30 de julho de 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-48/acsd-55566-mergecart-mutation-fails-with-an-internal-server-error-in-graphql-response">ACSD-55566: <code>mergeCart</code> mutação falha com erro interno do servidor na resposta do GraphQL:</a> O patch ACSD-55566 corrige o problema em que a mutação <code>mergeCart</code> falha com um erro interno do servidor na resposta do GraphQL. Este patch está disponível quando o <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.48 está instalado.  
    </td>
    <td>Novo artigo </td>
    <td>30 de julho de 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-48/acsd-56546-configurable-and-bundle-products-display-as-out-of-stock-on-the-storefront">ACSD-56546: os produtos configuráveis e agrupados são exibidos como esgotados na loja:</a> O patch ACSD-56546 corrige o problema em que os produtos configuráveis e agrupados são exibidos como esgotados na loja. Este patch está disponível quando o <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.48 está instalado.  
    </td>
    <td>Novo artigo </td>
    <td>30 de julho de 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-48/acsd-57565-the-order-dashboard-displays-incorrect-order-information">ACSD-57565: o painel de pedidos exibe informações de pedidos incorretas:</a> O patch ACSD-57565 corrige o problema em que o painel de pedidos exibe informações de pedidos incorretas até que o período seja atualizado. Este patch está disponível quando o <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.48 está instalado. 
    </td>
    <td>Novo artigo </td>
    <td>30 de julho de 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-48/acsd-57394-incorrect-product-sorting-by-multiple-sort-fields-in-graphql">ACSD-57394: classificação de produto incorreta por atributos de classificação múltipla no GraphQL:</a> O patch ACSD-57394 corrige o problema em que os produtos são classificados incorretamente ao usar vários atributos de classificação no GraphQL. Este patch está disponível quando o <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.48 está instalado. 
    </td>
    <td>Novo artigo </td>
    <td>30 de julho de 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-48/acsd-57854-graphql-response-contains-disabled-categories-that-should-not-be-listed-in-the-category-aggregations">ACSD-57854: a resposta do GraphQL contém categorias desabilitadas que não devem ser listadas nas agregações de categoria:</a> O patch ACSD-57854 corrige o problema em que a resposta do GraphQL contém categorias desabilitadas que não devem ser listadas nas agregações de categoria. Este patch está disponível quando o <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.48 está instalado. 
    </td>
    <td>Novo artigo </td>
    <td>30 de julho de 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-47/acsd-57074-yes-no-custom-attribute-does-not-work-with-indexing">ACSD-57074: o atributo personalizado Sim/Não com o prefixo <code>price_*</code> no atributo <code>attribute_code</code> não funciona com indexação:</a> O patch ACSD-57074 corrige o problema em que o atributo personalizado <em>Sim/Não</em> com o prefixo <code>price_*</code> no atributo <code>attribute_code</code> não funciona com indexação. Este patch está disponível quando o <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.47 está instalado. 
    </td>
    <td>Novo artigo </td>
    <td>30 de julho de 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-47/acsd-55241-used-and-times-used-attributes-display-incorrect-values-for-generated-coupons">ACSD-55241: os atributos Used e Times Used exibem valores incorretos para cupons gerados:</a> O patch ACSD-55241 corrige o problema em que os atributos Used e Times Used exibem valores incorretos para cupons gerados. Este patch está disponível quando o <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.47 está instalado. 
    </td>
    <td>Novo artigo </td>
    <td>30 de julho de 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-47/acsd-56760-admin-user-is-restricted-to-a-specific-website-and-is-unable-to-sort-or-add-new-products">ACSD-56760: o usuário administrador está restrito a um site específico e não pode classificar ou adicionar novos produtos:</a> O patch ACSD-56760 corrige o problema em que o usuário administrador, que está restrito a um site específico e não pode classificar ou adicionar novos produtos dentro de uma categoria, caso a loja da Web tenha sua própria categoria raiz. Este patch está disponível quando o <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.47 está instalado. 
    </td>
    <td>Novo artigo </td>
    <td>30 de julho de 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-48/acsd-56635-imported-customers-are-duplicated-with-the-same-email-address">ACSD-56635: os clientes importados são duplicados com o mesmo endereço de email quando o compartilhamento de conta é definido como Global:</a> O patch ACSD-56635 corrige o problema em que o cliente importado é duplicado com o mesmo endereço de email quando a importação é usada com o compartilhamento de conta definido como Global. Este patch está disponível quando o <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.48 está instalado. 
    </td>
    <td>Novo artigo </td>
    <td>30 de julho de 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-48/acsd-57315-new-transaction-created-in-paypal-payflow-pro-each-time-the-fetch-button-is-clicked">ACSD-57315: a nova transação é criada no PayPal Payflow Pro sempre que o botão buscar é clicado:</a> O patch ACSD-57315 corrige o problema em que uma nova transação é criada no PayPal Payflow Pro sempre que o botão buscar é clicado na tela exibir transação no Administrador. Este patch está disponível quando o <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.48 está instalado. 
    </td>
    <td>Novo artigo </td>
    <td>30 de julho de 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-48/acsd-56741-database-setup-upgrade-error-with-custom-mysql-trigger">ACSD-56741: Solucionando problemas de erros de configuração de banco de dados com gatilhos MySQL personalizados:</a> O patch ACSD-56741 corrige o problema em que uma mensagem de erro <em>Tentando acessar o deslocamento da matriz no valor do tipo nulo</em> aparece durante <code>setup:upgrade</code> devido a um gatilho MySQL personalizado no banco de dados não relacionado à indexação e ao MView. Este patch está disponível quando o <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.48 está instalado. 
    </td>
    <td>Novo artigo </td>
    <td>30 de julho de 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-48/acsd-58008-editing-the-end-date-as-empty-causes-the-schedule-update-to-disappear">ACSD-58008: editar a data final como vazia faz com que a atualização da programação desapareça:</a> O patch ACSD-58008 corrige o problema em que editar a data final como vazia faz com que a atualização da programação desapareça. Este patch está disponível quando o <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.48 está instalado. 
    </td>
    <td>Novo artigo </td>
    <td>30 de julho de 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-48/acsd-57337-admin-user-with-access-restrictions-can-see-companies">ACSD-57337: O usuário administrador com restrições de acesso pode exibir todas as empresas na grade Empresas:</a> O patch ACSD-57337 corrige o problema em que um usuário administrador com restrições de acesso a sites específicos pode exibir empresas de todos os sites na grade Empresas. Este patch está disponível quando o <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.48 está instalado. 
    </td>
    <td>Novo artigo </td>
    <td>30 de julho de 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/deployment/deployment-failed-with-correct-access-key-env-composer-auth">Falha na implantação com as chaves de acesso corretas em <code>env:COMPOSER_AUTH</code> ou <code>auth.json</code>:</a> Este artigo fornece uma solução para o problema quando a implantação falha com um erro como o do log de implantação. 
    </td>
    <td>Novo artigo </td>
    <td>30 de julho de 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/how-to-bypass-waf-for-graphql-requests">Como ignorar o WAF para solicitações do GraphQL:</a> Este artigo explica como ignorar solicitações do WAF para GraphQL quando o Fastly WAF estiver bloqueando solicitações do GraphQL. 
    </td>
    <td>Novo artigo </td>
    <td>30 de julho de 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/email-stating-that-export-storage-is-almost-full">Email informando que o armazenamento de exportações está quase cheio:</a> Este artigo fornece uma solução para o problema em que você recebe um email informando que o armazenamento de exportações está quase cheio. 
    </td>
    <td>Novo artigo </td>
    <td>30 de julho de 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/upgrade-mariadb-10-4-to-10-5-for-magento-commerce-cloud">Atualizar MariaDB 10.4 para 10.5 para Adobe Commerce na nuvem:</a> Este artigo explica como atualizar MariaDB 10.4 para 10.5 para continuar usando o Adobe Commerce na infraestrutura em nuvem. 
    </td>
    <td>Novo artigo </td>
    <td>30 de julho de 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/site-down-or-unresponsive/revised-patches-for-google-maps-access-loss-on-all-adobe-commerce-versions">Patches revisados para perda de acesso ao Google Maps em todas as versões do Adobe Commerce:</a> este artigo fornece uma correção para comerciantes do Adobe Commerce que não são compatíveis com nenhuma versão recente do Google Maps da versão 3.54+. 
    </td>
    <td>Novo artigo </td>
    <td>30 de julho de 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/security-update-available-for-adobe-commerce-apsb24-40-revised-to-include-isolated-patch-for-cve-2024-34102">Atualização de segurança disponível para o Adobe Commerce - APSB24-40:</a> Este artigo compartilha uma atualização relacionada ao CVE-2024-34102. 
    </td>
    <td>Novo artigo </td>
    <td>30 de julho de 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/poor-performance-in-integration-environments">Desempenho insatisfatório em ambientes de integração:</a> este artigo fornece uma solução para o problema em que os ambientes de integração Pro e os ambientes de preparo de Início têm um desempenho insatisfatório. 
    </td>
    <td>Novo artigo </td>
    <td>30 de julho de 2024</td>
 </tr>
</table>

## Artigos populares

* [Alternar para o OpenSearch para Adobe Commerce na nuvem 2.4.4](/help/announcements/adobe-commerce-announcements/switching-to-opensearch-for-adobe-commerce-on-cloud-2-4-4.md)
* [Vulnerabilidade do Apache log4j2 no Adobe Commerce](/help/announcements/adobe-commerce-announcements/apache-log4j2-adobe-commerce.md)
* [Atualizações de segurança disponíveis para o Adobe Commerce APSB22-12](/help/troubleshooting/known-issues-patches-attached/0-day-vulnerability-patch.md)
* [Identificar e medir paralisações do Adobe Commerce na infraestrutura em nuvem](/help/how-to/general/how-to-identify-outages.md)
* [Exibir a camada de vCPU do ambiente em seu cluster no Adobe Commerce](/help/how-to/general/check-vcpu-using-observation-for-adobe-commerce.md)
* [Adobe Commerce na infraestrutura em nuvem: cálculo de alocação de CPU](/help/how-to/general/magento-commerce-cloud-cpu-allocation-calculation.md)
* [Adobe Commerce na infraestrutura em nuvem: verificar a configuração da CPU do host](/help/how-to/general/magento-commerce-cloud-check-hosts-cpu-configuration.md)
