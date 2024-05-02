---
source-git-commit: 88a2b8fe11d718f33c26bbc6f407c55d9f1fd189
workflow-type: tm+mt
source-wordcount: '476'
ht-degree: 0%

---
# Guia de etiquetas da Base de Dados de Conhecimento

Este documento fornece diretrizes para adicionar rótulos aos artigos na Base de conhecimento de suporte da Adobe Commerce.
Os rótulos (também chamados de tags) melhoram a experiência de pesquisa no [Knowledge base de suporte do Adobe Commerce](https://support.magento.com/hc/en-us).
Os rótulos são adicionados no campo &quot;rótulos&quot; na seção de metadados de um arquivo de artigo, separados por vírgulas, sem espaço entre uma vírgula e o rótulo seguinte.
Consulte [../../.github/CONTRIBUTING.md#metadata] para obter detalhes.

## Disposições gerais

Para cada artigo, adicione os seguintes tipos de rótulo:

* Rótulo(s) do(s) produto(s). (obrigatório)
* Rótulo(s) das versões afetadas. (obrigatório, exceto artigos relacionados ao suporte geral)
* Rótulo para tipo de conteúdo. (obrigatório)
* Rótulos para os principais componentes tecnológicos.(se aplicável)
* Rótulos do processo/funcionalidade que está sendo solucionado/descrito. (se aplicável)
* Rótulos do problema que está sendo corrigido/descrito. (se aplicável)

Consulte as seções abaixo para obter recomendações detalhadas sobre como definir rótulos para cada um desses tipos de rótulos.

## Rótulos para produtos

<table>
<tbody>
  <tr>
    <th>Nome do produto</th>
    <th>Rótulo</th>
  </tr>
  <tr>
    <td>Adobe Commerce (todos os métodos de implantação) </td>
    <td>
    "Adobe Commerce,infraestrutura em nuvem,local"
    </td>
  </tr>
  <tr>
    <td>Adobe Commerce na infraestrutura em nuvem</td>
    <td>
      "Adobe Commerce, infraestrutura em nuvem"
    </td>
  </tr>
  <tr>
    <td>Adobe Commerce no local</td>
    <td>"Adobe Commerce, no local"</td>
  </tr>
  <tr>
    <td>Magento Business Intelligence (MBI)</td>
    <td>
        "Magento Business Intelligence,MBI"
    </td>
  </tr>
   <tr>
    <td>Magento Open Source</td>
    <td>
        "Magento Open Source"
    </td>
  </tr>
  <tr>
    <td>B2B para Adobe Commerce</td>
    <td>"B2B"</td>
  </tr>
  <tr>
    <td>PWA para Adobe Commerce</td>
    <td>"PWA"</td>
  </tr>
  <tr>
    <td>Projeto da loja Venia</td>
    <td>"Venia"</td>
  </tr>
  <tr>
    <td>Ferramenta de correções de qualidade, QPT</td>
    <td>"Ferramenta de correções de qualidade, correções QPT"</td>
  </tr>
  </tbody>
</table>

## Rótulos para versões de produtos

* Adicione um rótulo separado para cada versão do Adobe Commerce. Exemplo: &quot;2.3.7&quot;
* Não adicione rótulos para intervalos.
Ou seja, se 2.3.0 - 2.3.5 for afetado, adicione: &quot;2.3.0,2.3.1,2.3.2,2.3.2-p2,2.3.3,2.3.3-p1,2.3.4,2.3.4-p2,2.3.5-p1,2.3.5-p2&quot; NOT &quot;2.3.0 - 2.3.5&quot;
* Não adicione rótulos com .x. Exemplo: &quot;2.3.x&quot;

## Rótulos para tipo de conteúdo (com base na categoria)

<table>
  <tbody>
    <tr>
      <th>Categoria</th>
      <th>Rótulo</th>
    </tr>
    <tr>
      <td>Práticas recomendadas</td>
      <td>"práticas recomendadas" (não "prática recomendada" nem "prática recomendada")</td>
    </tr>
    <tr>
      <td>
        Solução de problemas
      </td>
      <td>
      "solução de problemas"
      </td>
    </tr>
    <tr>
      <td>Como</td>
      <td>"como"</td>
    </tr>
    <tr>
      <td>Perguntas frequentes</td>
      <td >"Perguntas frequentes"</td>
    </tr>
  </tbody>
</table>

## Etiquetas para os principais componentes técnicos

* Use as letras maiúsculas de acordo com o nome oficial do componente.
* Não use sinônimos, um rótulo para um componente.
* É preferível usar um rótulo de palavra, mas se o nome do componente contiver várias palavras, use várias palavras. Não adicione descrições de problemas. Ou seja, coloque &quot;Elasticsearch&quot; em vez de &quot;Elasticsearch problems&quot;.
* Se o conteúdo for relevante somente para uma versão específica do componente, adicione um rótulo contendo name + version.\
  Exemplo: &quot;Elasticsearch 5&quot;. Se for relevante para várias versões específicas, adicione vários rótulos desse tipo. Exemplo: &quot;Elasticsearch 5&quot;, &quot;Elasticsearch 6&quot;. Quando pertinente, use &quot;x&quot; para várias versões. Exemplo: &quot;Elasticsearch 2.x&quot;

Exemplos:

* &quot;Elasticsearch&quot;
* &quot;New Relic&quot;
* &quot;Assistente de configuração da Web&quot;

## Rótulos do processo/funcionalidade que está sendo solucionado/descrito

* Use letras minúsculas, com exceção dos substantivos próprios.
* Não use sinônimos, um rótulo para uma entidade.
* É preferível usar um rótulo de palavra. Não adicione a descrição do problema. Ou seja, coloque &quot;banco de dados&quot; em vez de &quot;falhas de banco de dados&quot;.

Exemplos: 

* &quot;banco de dados&quot;
* &quot;cron&quot;
* &quot;implantação&quot;
* &quot;atualização em massa&quot;

## Rótulos do problema que está sendo corrigido/descrito

* Use letras minúsculas, com exceção dos substantivos próprios.
* Não use sinônimos, um rótulo para uma entidade.
* É preferível usar um rótulo de palavra. Não converta uma mensagem de erro em um rótulo.

Exemplos:

* &quot;site inativo&quot;
* &quot;Erro 500&quot;
* &quot;cron preso&quot;
