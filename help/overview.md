---
title: Knowledge base de suporte do Adobe Commerce
description: Tudo o que você precisa saber para solucionar problemas e manter sua loja da Commerce.
exl-id: feacf38f-2803-4170-a64f-5d7c4567432d
feature: Support
role: Admin
source-git-commit: 607b835da518536196654734f62d78d095099476
workflow-type: tm+mt
source-wordcount: '1615'
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
    <a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-25075">A Ferramenta de Verificação de Segurança retorna "Não é possível determinar se o servidor usa 2FA":</a> Para resolver o erro, verifique se o módulo <code>Magento_TwoFactorAuth</code> foi desabilitado. Para ser aprovado na verificação, em geral, ele deve estar ativado.
    </td>
    <td>Novo artigo </td>
    <td>17 de outubro de 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-51/acsd-60632-address-saved-on-every-order-attempt">ACSD-60632: Endereço salvo com cada tentativa de pedido:</a> O patch ACSD-60632 corrige o problema em que um novo endereço é salvo com cada tentativa de posicionamento de pedido, independentemente do pedido ser criado com êxito ou não. Este patch está disponível quando o [!DNL Quality Patches Tool (QPT)] 1.1.51 está instalado.
    </td>
    <td>Novo artigo </td>
    <td>17 de outubro de 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-51/acsd-60326-graphql-query-error-customer-return-status">ACSD-60326: a consulta do GraphQL sobre o status Retornos do cliente fornece um erro:</a> O patch ACSD-60326 corrige o problema em que ocorre um erro na consulta do GraphQL sobre o status Retornos do cliente. Este patch está disponível quando o [!DNL Quality Patches Tool (QPT)] 1.1.51 está instalado.
    </td>
    <td>Novo artigo </td>
    <td>17 de outubro de 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-52/acsd-59925-sorting-items-in-media-gallery">ACSD-59925: Classificando itens na Galeria de Mídia por posição no GraphQL:</a> O patch ACSD-59925 corrige o problema em que os itens na Galeria de Mídia não são classificados por posição, levando a uma ordem de exibição incorreta. Este patch está disponível quando o [!DNL Quality Patches Tool (QPT)] 1.1.52 está instalado.
    </td>
    <td>Novo artigo </td>
    <td>17 de outubro de 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-52/acsd-61322-products-not-assigned-to-shared-catalogue">ACSD-61322: os produtos não atribuídos ao Catálogo Compartilhado estão incluídos no Mapa de Site XML:</a> O patch ACSD-61322 corrige o problema em que produtos/categorias não atribuídos ao Catálogo Compartilhado para o grupo Padrão (Geral) ainda estão incluídos no Mapa de Site XML. Este patch está disponível quando o [!DNL Quality Patches Tool (QPT)] 1.1.52 está instalado.
    </td>
    <td>Novo artigo </td>
    <td>17 de outubro de 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-52/acsd-60590-optimized-bestseller-report-generation">ACSD-60590: Melhorando o desempenho da geração de Relatórios diários agregados dos melhores vendedores:</a> O patch ACSD-60590 corrige o problema em que o Relatório diário agregado dos melhores vendedores leva um tempo significativo para ser gerado para um grande volume de pedidos feitos. Este patch está disponível quando o [!DNL Quality Patches Tool (QPT)] 1.1.52 está instalado.
    </td>
    <td>Novo artigo </td>
    <td>17 de outubro de 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-52/acsd-59865-cart-price-rule-fix-for-insufficient-quantity-issue">ACSD-59865: a Regra de Preço do Carrinho não cancela as regras anteriores devido à quantidade insuficiente do produto:</a> O patch ACSD-59865 corrige o problema em que o <em>Valor da etapa de quantidade de desconto</em> em <em>Desconto de valor fixo</em>, <em>Percentual de desconto do preço do produto</em> e <em>Comprar X obter Y</em> As Regras de Preço do Carrinho não cancelam mais a ação das regras anteriores. Este patch está disponível quando o [!DNL Quality Patches Tool (QPT)] 1.1.52 está instalado.
    </td>
    <td>Novo artigo </td>
    <td>17 de outubro de 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/error-when-filtering-orders-in-admin">Erro ao filtrar pedidos no Administrador:</a> Este artigo fornece um patch para o problema do Adobe Commerce em que ocorre um erro ao tentar filtrar pedidos no Administrador por data, exibindo a mensagem: <em>Violação de restrição de integridade: 1052 Coluna 'created_at' onde a cláusula é ambígua</em>.
    </td>
    <td>Novo artigo </td>
    <td>17 de outubro de 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-25030">Adobe Commerce: Problemas do JavaScript em linha na página de check-out no modo restrito da Política de Segurança de Conteúdo (CSP):</a> Este artigo fornece explicações e soluções detalhadas para problemas encontrados com o JavaScript personalizado adicionado pelo Administrador da Adobe Commerce e pelo Gerenciador de Tags da Google no Adobe Commerce 2.4.7 durante o check-out quando o <strong>modo restrito da CSP</strong> está habilitado.
    </td>
    <td>Novo artigo </td>
    <td>17 de outubro de 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-51/acsd-61195-empty-cart-on-final-graphql-page">ACSD-61195: a solicitação do GraphQL do carrinho falha ao retornar itens na página final:</a> O patch ACSD-61195 corrige o problema em que nenhum item do carrinho é retornado na última página da solicitação do GraphQL do carrinho. Este patch está disponível quando o [!DNL Quality Patches Tool (QPT)] 1.1.51 está instalado.
    </td>
    <td>Novo artigo </td>
    <td>17 de outubro de 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-50/acsd-59514-forms-in-admin-with-page-builder-throw-error-in-browser-console">ACSD-59514: Forms no Admin com Page Builder gera um erro no console do navegador:</a> O patch ACSD-59514 corrige o problema em que os formulários no Admin com Page Builder geram o erro <em>O Page Builder foi renderizado por 5 segundos sem liberar bloqueios</em> no console do navegador após o envio do formulário, e as alterações não podem ser salvas. Este patch está disponível quando o [!DNL Quality Patches Tool (QPT)] 1.1.50 está instalado.
    </td>
    <td>Novo artigo </td>
    <td>17 de outubro de 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-51/acsd-60538-if-product-is-disabled-attributes-dont-show">ACSD-60538: os atributos não aparecem corretamente se o produto estiver desabilitado em <em>Todas as Exibições da Loja</em>:</a> O patch ACSD-60538 corrige o problema em que, se um produto estiver desabilitado em <em>Todas as Exibições da Loja</em> e habilitado somente em escopos específicos de exibição da loja, os atributos do produto não aparecem corretamente na resposta do GraphQL, fazendo com que o produto não seja exibido corretamente. Este patch está disponível quando o [!DNL Quality Patches Tool (QPT)] 1.1.51 está instalado.
    </td>
    <td>Novo artigo </td>
    <td>17 de outubro de 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-50/acsd-58352-return-attribute-labels-for-the-default-store-are-returned-via-graphql-api">ACSD-58352: Os rótulos de atributo de retorno para o armazenamento padrão são retornados por meio da API do GraphQL:</a> O patch ACSD-58352 corrige o problema em que os rótulos de atributo de retorno para o armazenamento padrão são retornados por meio da API do GraphQL quando uma exibição de armazenamento não padrão é especificada no cabeçalho da solicitação. Este patch está disponível quando o [!DNL Quality Patches Tool (QPT)] 1.1.50 está instalado.
    </td>
    <td>Novo artigo </td>
    <td>17 de outubro de 2024</td>
  </tr>

<tr>
    <td>
    <a href = "https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-24983">A lista suspensa <em>Trocar Contas</em> está ausente em sua conta:</a> Este artigo fornece uma solução para o problema do Adobe Commerce em que a lista suspensa <em>Trocar Contas</em> está ausente em sua conta, e você perdeu o acesso para enviar tíquetes em nome do comerciante.
    </td>
    <td>Novo artigo</td>
    <td>17 de outubro de 2024</td>
  </tr>

<tr>  
    <td>
    <a href = "https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-49/acsd-56979-product-images-removed-after-staging-update-deleted">ACSD-56979: imagens de produto removidas após atualização de preparo excluída:</a> O patch ACSD-56979 corrige o problema em que as imagens de produto são removidas após a exclusão de uma atualização de preparo. Este patch está disponível quando o [!DNL Quality Patches Tool (QPT)] 1.1.49 está instalado.  
    </td>
    <td>Novo artigo</td>
    <td>17 de outubro de 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-50/acsd-48210-store-view-specific-scope-attribute-overrides-global-values">ACSD-48210: os atributos de escopo específicos da exibição de armazenamento substituem os valores globais:</a> O patch ACSD-48210 corrige o problema em que, ao atualizar um atributo <em>Escopo de Site</em> em uma exibição de armazenamento específica, substitui os valores de atributo no escopo global. Este patch está disponível quando o [!DNL Quality Patches Tool (QPT)] 1.1.50 está instalado. 
    </td>
    <td>Novo artigo </td>
    <td>17 de outubro de 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-50/acsd-59280-fix-for-reflection-union-type-error">ACSD-59280: erro RefletionUnionType::getName() em instalações 2.4.4-pX:</a> O patch ACSD-59280 corrige o problema em que o erro de chamada para o método indefinido <code>ReflectionUnionType::getName()</code> ocorre durante a instalação das versões 2.4.4-pX. Este patch está disponível quando o [!DNL Quality Patches Tool (QPT)] 1.1.50 está instalado. 
    </td>
    <td>Novo artigo </td>
    <td>17 de outubro de 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-50/acsd-54887-customer-shopping-cart-gets-cleared-after-session-expiry">ACSD-54887: o carrinho de compras do cliente é limpo após a expiração da sessão do cliente:</a> O patch ACSD-54887 corrige o problema em que o carrinho de compras do cliente é limpo após a expiração da sessão do cliente com o <em>Carrinho de compras persistente</em> habilitado. Este patch está disponível quando o [!DNL Quality Patches Tool (QPT)] 1.1.50 está instalado. 
    </td>
    <td>Novo artigo </td>
    <td>17 de outubro de 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-50/acsd-60303-admin-order-placement-fix">ACSD-60303: problema de posicionamento de pedido de administrador resolvido com a minificação de HTML habilitada:</a> O patch ACSD-60303 corrige o problema em que um pedido do Administrador não pode ser feito se a minificação de HTML estiver habilitada. Este patch está disponível quando o [!DNL Quality Patches Tool (QPT)] 1.1.50 está instalado. 
    </td>
    <td>Novo artigo </td>
    <td>17 de outubro de 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-49/acsd-57045-url-rewrites-cause-infinite-page-looping-after-website-root-unchecked-hierarchy">ACSD-57045: as regravações de URL causam looping de página infinito depois que a <em>Raiz do Site</em> é desmarcada da Hierarquia:</a> O patch ACSD-57045 corrige o problema em que as regravações de URL causam looping de página infinito depois que a <em>Raiz do Site</em> é desmarcada da Hierarquia. Este patch está disponível quando o [!DNL Quality Patches Tool (QPT)] 1.1.49 está instalado.
    </td>
    <td>Novo artigo </td>
    <td>17 de outubro de 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-49/ascd-58446-deleting-a-team-with-child-users-or-teams-via-graphql-gives-an-uninformative-error-message">ACSD-58446: excluir uma equipe com usuários ou equipes filho por meio do GraphQL gera uma mensagem de erro não informativa:</a> O patch ACSD-58446 corrige o problema do Adobe Commerce em que a exclusão de uma equipe com usuários ou equipes filho por meio do GraphQL retorna uma mensagem de erro não informativa inconsistente com a interface. Este patch está disponível quando o [!DNL Quality Patches Tool (QPT)] 1.1.49 está instalado. 
    </td>
    <td>Novo artigo </td>
    <td>17 de outubro de 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-49/acsd-58375-wrong-youtube-api-key-configuration-causes-an-error-when-adding-a-youtube-video-at-the-store-view-level">ACSD-58735: a chave de API do YouTube configurada incorretamente causa erro ao adicionar vídeo no nível de exibição da loja:</a> O patch ACSD-58735 corrige o problema em que a configuração incorreta da chave de API do YouTube causa um erro ao adicionar um vídeo do YouTube no nível de exibição da loja. Este patch está disponível quando o [!DNL Quality Patches Tool (QPT)] 1.1.49 está instalado. 
    </td>
    <td>Novo artigo </td>
    <td>17 de outubro de 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-49/acsd-57086-orders-placed-from-non-default-websites-with-terms-conditions-processed-incorrectly">ACSD-57086: pedidos de sites não padrão com termos e condições habilitados são processados incorretamente:</a> O patch ACSD-57086 corrige o problema em que os pedidos feitos de sites não padrão com termos e condições habilitados não são processados corretamente. Este patch está disponível quando o [!DNL Quality Patches Tool (QPT)] 1.1.49 está instalado. 
    </td>
    <td>Novo artigo </td>
    <td>17 de outubro de 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-50/acsd-58141-phpsessid-regenerates-on-post-requests-for-logged-in-customers-with-l2-redis-cache-enabled">ACSD-58141: PHPSESSID é gerado novamente nas solicitações do POST para clientes conectados se o cache L2 Redis estiver habilitado:</a> O patch ACSD-58141 corrige o problema em que o PHPSESSID é regenerado nas solicitações do POST para um cliente conectado se o cache L2 Redis estiver habilitado e o cliente for atualizado pelo administrador. Este patch está disponível quando o [!DNL Quality Patches Tool (QPT)] 1.1.50 está instalado. 
    </td>
    <td>Novo artigo </td>
    <td>17 de outubro de 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-50/acsd-58790-fixes-pinch-to-zoom-functionality-on-the-product-detail-page-images-in-mobile-view-on-chrome">ACSD-58790: corrige a funcionalidade de pinçar para zoom nas imagens da página de detalhes do produto na exibição móvel no Chrome:</a> O patch ACSD-58790 corrige o problema do Adobe Commerce em que a imagem na exibição móvel no Chrome não dava zoom na imagem conforme esperado. Este patch está disponível quando o [!DNL Quality Patches Tool (QPT)] 1.1.50 está instalado. 
    </td>
    <td>Novo artigo </td>
    <td>17 de outubro de 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-50/acsd-58442-fixes-issue-devices-768px-mobile-view-instead-desktop">ACSD-58442: corrige o problema em que dispositivos com largura de 768px são tratados como móveis, fazendo com que o menu e o cabeçalho sejam carregados no modo de exibição móvel e não na área de trabalho:</a> O patch ACSD-58442 corrige o problema do Adobe Commerce em que dispositivos com largura de 768px são tratados como móveis, fazendo com que o menu e o cabeçalho sejam carregados em um modo de exibição móvel em vez de em um desktop. Este patch está disponível quando o [!DNL Quality Patches Tool (QPT)] 1.1.50 está instalado.
    </td>
    <td>Novo artigo </td>
    <td>17 de outubro de 2024</td>
  </tr>
</table>
