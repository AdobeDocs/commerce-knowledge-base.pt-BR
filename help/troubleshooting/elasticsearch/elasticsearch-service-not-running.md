---
title: O serviço Elasticsearch não está em execução
description: Este artigo fornece soluções para erros que podem ocorrer quando o serviço Elasticsearch (ES) não está em execução (geralmente devido a uma falha). Os sintomas podem incluir erros ao executar verificações de integridade usando curl, reindexação usando a linha de comando, erros de Exceção e PHP e erros nas páginas do produto. A tabela lista erros e links para recursos para tentar resolvê-los. Um sintoma pode ter várias causas diferentes.
exl-id: 2c2230de-cb30-4a03-8c3e-d9f44783dbae
source-git-commit: 3ff881f1c799201ed25ba9737864b1226d283c22
workflow-type: tm+mt
source-wordcount: '496'
ht-degree: 0%

---

# O serviço Elasticsearch não está em execução

Este artigo fornece soluções para erros que podem ocorrer quando o serviço Elasticsearch (ES) não está em execução (geralmente devido a uma falha). Os sintomas podem incluir erros ao executar verificações de integridade usando curl, reindexação usando a linha de comando, erros de Exceção e PHP e erros nas páginas do produto. A tabela lista erros e links para recursos para tentar resolvê-los. Um sintoma pode ter várias causas diferentes.

## Compatibilidade de versão do Elasticsearch com o Adobe Commerce

* Adobe Commerce no local e Adobe Commerce na infraestrutura em nuvem:

   * A v2.2.3+ é compatível com ES 5.x
   * As versões 2.2.8+ e v2.3.1+ são compatíveis com ES 6.x
   * As versões 2.x e 5.x do ES não são recomendadas devido ao [Fim da vida útil](https://www.elastic.co/support/eol). No entanto, se você tiver o Adobe Commerce v2.3.1 e quiser usar o ES 2.x ou o ES 5.x, você deve [Alterar o Elasticsearch php Client](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/es-downgrade.html).

* O Magento Open Source v2.3.0+ é compatível com ES 5.x e 6.x (mas recomenda-se o 6.x).

<table>
<tr>
<th>Sintomas quando o serviço ES não está em execução</th>
<th>Detalhes</th>
<th>Recursos</th>
</tr>
<tr>
<td rowspan="3">Erros de exceção</td>
</tr>
<tr>
<td>
<code>{"0":"{\"error\":{\"root_cause\":[{\"type\":\"illegal_argument_exception\",\"reason\":\"Fielddata is disabled on text fields by default. Set fielddata=true on [%attribute_code%]] in order to load fielddata in memory by uninverting the inverted index. Note that this can however use significant memory.\"}]</code>
</td>
<td>
O <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/elasticsearch/elasticsearch-5-is-configured-but-search-page-does-not-load-with-fielddata-is-disabled...-error.html">Elasticsearch 5 está configurado, mas a página de pesquisa não carrega com o erro "Fielddata is disabled..."</a> em nossa base de dados de suporte.
</td>
</tr>
<tr>
<td>
<code>Elasticsearch\Common\Exceptions\NoNodesAvailableException: Noticed exception 'Elasticsearch\Common\Exceptions\NoNodesAvailableException' with message 'No alive nodes found in your cluster' in /app/&lt;projectid&gt;/vendor/elasticsearch/elasticsearch/src/Elasticsearch/ConnectionPool/StaticNoPingConnectionPool.php:51</code>
</td>
<td>
Índices Elasticsuite não sendo excluídos.  Consulte <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/elasticsearch/elasticsuite-tracking-indices-causes-problems-with-elasticsearch.html">Os índices de rastreamento do ElasticSuite causam problemas com o Elasticsearch</a> em nossa base de dados de conhecimento de suporte.
 </td>
</tr>
<tr>
<td>Erro de PHP</td>
<td>
<i>Nenhum nó ativo encontrado no cluster","1":"#0 /app/&lt;projectid&gt;/vendor/elasticsearch/elasticsearch/src/Elasticsearch/Transport.php</i>
</td>
<td rowspan="4">
<ul>
<li>Recursos para espaço em disco insuficiente:<ul>
<li><a href="https://www.cyberciti.biz/datacenter/linux-unix-bsd-osx-cannot-write-to-hard-disk/">8 dicas para solucionar problemas de disco rígido nos sistemas Linux e Unix, como disco cheio ou não pode gravar no disco</a></li>
<li><a href="https://serverfault.com/questions/315181/df-says-disk-is-full-but-it-is-not">serverfault: df diz que o disco está cheio, mas não está</a></li>
<li><a href="https://unix.stackexchange.com/questions/125429/tracking-down-where-disk-space-has-gone-on-linux">unix.stackexchange.com: rastreando para onde o espaço em disco foi no Linux?</a></li>
<li>Os arquivos de log não são arquivados regularmente. Consulte <a href="https://docs.magento.com/m2/ee/user_guide/system/action-log-archive.html#configure-the-log-archive">Configurar o Arquivo de Log</a> na documentação do desenvolvedor.</li>
<li>Os diretórios do sistema de arquivos não estão otimizados. Consulte <a href="https://docs.magento.com/m2/ee/user_guide/system/file-optimization.html">Otimização de arquivos</a> na documentação do desenvolvedor.</li>
<li>Se as soluções na documentação acima não resolverem o problema, entre em contato com a equipe de conta da Adobe para solicitar armazenamento adicional.</li>
</ul>
</li>
<li>Se o disco não estiver sem espaço de armazenamento, mas você ainda receber mensagens de erro na coluna esquerda, <a href="/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket">envie um tíquete de suporte</a>.</li>
</ul>
<ul>
<li>Consulte <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/elasticsearch/elasticsuite-tracking-indices-causes-problems-with-elasticsearch.html">Os índices de rastreamento do ElasticSuite causam problemas com o Elasticsearch</a> em nossa base de dados de conhecimento de suporte.
</li>
</ul>
</td>
</tr>
<tr>
<td><code>Curl</code> erro</td>
<td>A execução do comando <code>curl</code> para verificar a integridade do Elasticsearch:<code>curl -m1 localhost:9200/_cluster/health?pretty</code>(ou<code>curl -m1 elasticsearch.internal:9200/_cluster/health?pretty</code>para contas de Início) produz este erro: <i>Erro: curl: (7) Falha ao conectar à porta localhost 9200: Conexão recusada</i> </td>
</tr>
<tr>
<td>Erro de linha de comando</td>
<td>A execução de <code>$ bin/magento indexer:reindex catalogsearch_fulltext</code> produz este erro <i>Erro desconhecido no processo do indexador da Pesquisa no Catálogo:
        Nenhum nó ativo encontrado no cluster</i>
</td>
</tr>
<tr>
<td>Erro nas páginas do produto
</td>
<td><i>Ocorreu um erro ao processar sua solicitação.
      A impressão de exceção está desabilitada por padrão por motivos de segurança</code></i>
</tr>
</table>
