---
title: O mecanismo de pesquisa do catálogo MySQL será removido no Adobe Commerce 2.4.0
description: O Adobe Commerce no local, o Adobe Commerce na infraestrutura em nuvem e o Magento Open Source 2.4.0 serão lançados nos próximos meses. Para o Adobe Commerce no local e o Magento Open Source versão 2.4.0, o Elasticsearch 6.x ou 7.x será um componente obrigatório e o mecanismo de pesquisa MySQL será removido. No Adobe Commerce na infraestrutura em nuvem, o Elasticsearch já é necessário.
exl-id: 717be515-3cbf-42e9-9b72-caf11b8c3771
feature: Catalog Management, Search, Services
role: Admin
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '563'
ht-degree: 0%

---

# O mecanismo de pesquisa do catálogo MySQL será removido no Adobe Commerce 2.4.0

O Adobe Commerce no local, o Adobe Commerce na infraestrutura em nuvem e o Magento Open Source 2.4.0 serão lançados nos próximos meses. Para o Adobe Commerce no local e o Magento Open Source versão 2.4.0, o Elasticsearch 6.x ou 7.x será um componente obrigatório e o mecanismo de pesquisa MySQL será removido. No Adobe Commerce na infraestrutura em nuvem, o Elasticsearch já é necessário.

>[!WARNING]
>
>Falhar ao instalar/configurar o Elasticsearch 6/7 antes de tentar atualizar pode causar problemas sérios com o Adobe Commerce. Observe que as atualizações de serviço na Adobe Commerce na infraestrutura em nuvem não podem ser enviadas para o ambiente de produção sem aviso prévio de 48 horas úteis para nossa equipe de infraestrutura. Isso é necessário, pois precisamos garantir que tenhamos um engenheiro de suporte de infraestrutura disponível para atualizar sua configuração dentro de um prazo desejado com tempo de inatividade mínimo para seu ambiente de produção. Portanto, 48 horas antes de quando suas alterações precisam estar em produção [enviar um tíquete de suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) detalhando o upgrade de serviço necessário e informando o horário em que você deseja que o processo de upgrade tenha início.

O motivo para a remoção do mecanismo de pesquisa MySQL é que o Elasticsearch fornece recursos de pesquisa superiores, bem como otimizações de desempenho do catálogo.

## Produtos e versões afetados:

* Adobe Commerce no local v2.4.0
* Magento Open Source v2.4.0

## Atualizando:

<table style="height: 164px; width: 632.2px;">
<tbody>
<tr>
<td class="wysiwyg-text-align-center" style="width: 133px;"><strong>Mecanismo de pesquisa</strong></td>
<td class="wysiwyg-text-align-center" style="width: 478.2px;"><strong>Ação</strong></td>
</tr>
<tr>
<td class="wysiwyg-text-align-center" style="width: 133px;">MySQL</td>
<td style="width: 478.2px;">Você deve instalar o Elasticsearch. Consulte <a href="https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/es-overview.html">Instalar e configurar o Elasticsearch</a> na documentação do desenvolvedor.</td>
</tr>
<tr>
<td class="wysiwyg-text-align-center" style="width: 133px;">Elasticsearch (sem versão listada)</td>
<td style="width: 478.2px;">Você está usando o Elasticsearch 2 e deve atualizar para o Elasticsearch 7 (preferencial) ou 6. Consulte <a href="https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/es-overview.html#es-upgrade6">Atualizando o Elasticsearch</a> e <a href="https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/configure-magento.html">Configurar o Commerce para usar o Elasticsearch</a> na documentação do desenvolvedor para obter detalhes.</td>
</tr>
<tr>
<td class="wysiwyg-text-align-center" style="width: 133px;">ELASTICSEARCH 5</td>
<td style="width: 478.2px;">O Elasticsearch 5 atingiu seu <a href="https://www.elastic.co/support/eol">Fim da vida útil</a> e foi descontinuado no Adobe Commerce 2.4.0. Atualize para o Elasticsearch 7 (preferencial) ou 6.</td>
</tr>
<tr>
<td class="wysiwyg-text-align-center" style="width: 133px;">Elasticsearch 6 ou 7</td>
<td style="width: 478.2px;">Não é necessário executar etapas adicionais antes de atualizar para o Adobe Commerce 2.4.0.</td>
</tr>
<tr>
<td class="wysiwyg-text-align-center" style="width: 133px;">Extensão de terceiros</td>
<td style="width: 478.2px;">Não é necessário instalar o Elasticsearch. A Adobe Commerce recomenda que você entre em contato com o fornecedor do mecanismo de pesquisa para determinar se sua extensão é totalmente compatível com o Adobe Commerce 2.4.0.</td>
</tr>
</tbody>
</table>

## Instalação:

Quando o Adobe Commerce no local e o Magento Open Source 2.4.0 for lançado, o Elasticsearch será um componente obrigatório, portanto, você deve ter uma configuração de host Elasticsearch e configurada antes da instalação da versão 2.4.0. Consulte [Instalar e configurar o Elasticsearch](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/es-overview.html) na documentação do desenvolvedor.

Por padrão, a pesquisa no Adobe Commerce usará o Elasticsearch 7 como mecanismo de pesquisa e tentará se conectar a um servidor em localhost:9200. Elasticsearch 6.x também é suportado. Se a configuração não corresponder aos padrões, é possível definir essas configurações usando argumentos passados para `setup:install`, da mesma forma que a conexão de banco de dados é configurada.

Por exemplo, `setup:install --elasticsearch-host=es.mystore.com`

Durante a instalação, a conexão de Elasticsearch será verificada e a instalação falhará se o Adobe Commerce não conseguir se conectar a um host de Elasticsearch. Se isso ocorrer, verifique se o Elasticsearch está ativo e em execução e se você forneceu os parâmetros de conexão corretos.
