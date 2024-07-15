---
title: Knowledge base de suporte do Adobe Commerce
description: Tudo o que você precisa saber para solucionar problemas e manter sua loja da Commerce.
exl-id: feacf38f-2803-4170-a64f-5d7c4567432d
feature: Support
role: Admin
source-git-commit: 95509b717d41436b68ad94c3c28ac72e1887fdfc
workflow-type: tm+mt
source-wordcount: '639'
ht-degree: 1%

---

# Knowledge base de suporte do Adobe Commerce

![Página inicial da Base de Dados de Conhecimento](../help/assets/knowledge-base-home-page-cover.jpg){width="100%"}

As informações nesta Base de Dados de Conhecimento foram criadas como complementares à [Documentação do Desenvolvedor do Adobe Commerce](https://developer.adobe.com/commerce/docs), ao [Guia do Comerciante do Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-admin/user-guides/home.html) e a outras publicações da Adobe Commerce. Ele aborda a solução de problemas e as práticas recomendadas, anúncios de hosts, responde às perguntas frequentes e destaca cenários específicos que não foram mencionados (por qualquer motivo) na documentação oficial.

## O que há na Knowledge Base?

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
    <a href = "https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/how-to-update-the-cloud-account-profile">Como atualizar o perfil da conta da nuvem:</a> Este artigo fornece etapas sobre como modificar o perfil na conta da nuvem.
    </td>
    <td>Novo artigo</td>
    <td>22 de abril de 2024</td>
  </tr>

<td>
    <a href = "https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/payments/admin-create-order-page-in-csp-restricted-mode">Solução de problemas para criar uma página de ordem no modo restrito do CSP:</a> este artigo fornece explicações e correções para problemas do Adobe Commerce 2.4.7 ao criar uma ordem no lado do Administrador quando o modo restrito do CSP estiver <em>Habilitado</em>.  
    </td>
    <td>Novo artigo</td>
    <td>22 de abril de 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/payments/storefront-checkout-page-in-csp-restricted-mode">Solucionar problemas da página de check-out da loja no modo restrito do CSP:</a> Este artigo fornece explicações e correções para problemas do Adobe Commerce 2.4.7 ao visualizar a página de check-out no modo restrito do CSP, com a mensagem de erro <em>"Recusado a executar o script incorporado porque viola a seguinte diretiva de Política de Segurança de Conteúdo: "script-src ..."</em> no log de console do navegador. 
    </td>
    <td>Novo artigo </td>
    <td>22 de abril de 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-46/acsd-54656-invisible-recaptcha-fails-during-checkout-preventing-order-placement">ACSD-54656: o reCAPTCHA invisível não está funcionando durante o check-out, impedindo o posicionamento do pedido:</a> O patch ACSD-54656 corrige o problema em que o reCAPTCHA invisível não está funcionando corretamente durante o check-out, impedindo o posicionamento de um pedido. Este patch está disponível quando o <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.46 está instalado. 
    </td>
    <td>Novo artigo </td>
    <td>22 de abril de 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-46/acsd-46767-category-page-caches-invalidate-when-the-stock-quantity-changes">ACSD-46767: os caches de página de categoria são invalidados quando a quantidade de estoque é alterada:</a> O patch ACSD-46767 corrige o problema em que os caches de página de categoria são invalidados quando a quantidade de estoque é alterada, mesmo que o produto ainda esteja em estoque. Este patch está disponível quando o <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.46 está instalado.  
    </td>
    <td>Novo artigo </td>
    <td>22 de abril de 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-45/acsd-56415-performance-of-partial-price-indexing-is-slowed-down-due-to-a-delete-query">ACSD-56415: O desempenho da Indexação de Preço Parcial está lento devido à consulta de DELETE:</a> O patch ACSD-56415 corrige o problema em que o desempenho da Indexação de Preço Parcial está lento devido a uma consulta de DELETE quando o banco de dados tem muito índice de dados de preço parcial. Este patch está disponível quando o <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.45 está instalado.  
    </td>
    <td>Novo artigo </td>
    <td>22 de abril de 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-47/acsd-56858-role-permissions-display-issue-in-b2b-company-admin-panel">ACSD-56858: discrepância de permissões de função no administrador da empresa B2B:</a> O patch ACSD-56858 corrige o problema em que as permissões de função são exibidas incorretamente para um administrador de empresa restrito no ambiente B2B. Este patch está disponível quando o <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.47 está instalado. 
    </td>
    <td>Novo artigo </td>
    <td>22 de abril de 2024</td>
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
