---
source-git-commit: c992521cae8c847adc0cc23d2323300e0ba69cdc
workflow-type: tm+mt
source-wordcount: '1023'
ht-degree: 0%

---
# Guia de Estilo da Base de Dados de Suporte

Siga estas recomendações de estilo e formatação ao contribuir com a Central de ajuda da Adobe Commerce.

## Títulos

* Os títulos estão em maiúsculas como na norma culta.
* Plural para títulos; singular para cabeçalhos de procedimento. Exemplo: Título - Escrever livros. Cabeçalho - Escreva um livro.
* Mantenha os títulos curtos, com palavras importantes no início. Por motivos de SEO, é altamente recomendado que os títulos não tenham mais de 70 caracteres (há uma exceção quando uma redução de título impede que o verdadeiro significado seja comunicado). 

## Cabeçalhos

* O cabeçalho de nível superior é H2. (H1 é, por padrão, o título do artigo, mesmo que o título não esteja visivelmente formatado com H1).
* Use verbos infinitivos para cabeçalhos de tarefas. Por exemplo, &quot;Como identificar eventos de alto tráfego&quot;.
* Use o formulário no singular para cabeçalhos de tarefas. Por exemplo, &quot;Estrutura de módulo&quot;.
* Evite cabeçalhos duplos (deve haver pelo menos uma frase entre os cabeçalhos).
* Uso de maiúsculas como sentença em todos os cabeçalhos.
* Os títulos das tarefas são fundamentais (&quot;Criar x&quot;, não &quot;Criar x&quot; ou &quot;Criar x&quot;).

## Listas

* Etapas em uma tarefa: máximo de 9

* As listas com marcadores facilitam a digitalização.

   * Use listas com marcadores para métodos, abordagens, opções e etapas de tarefas não consecutivas.
   * Manter texto em marcadores curtos, de preferência não mais do que duas frases.
   * Minimize o número de marcadores; sete ou menos é ideal.
   * Evite colocar uma dica ou nota entre itens com marcadores.
   * Use a estrutura de gramática paralela em listas, mas quebre essa regra se resultar em excesso de verbidades ou linguagem distorcida.
   * Use letra maiúscula na primeira palavra de cada item em uma lista com marcadores, mesmo que seja um fragmento.

* Torne suas listas paralelas. Por exemplo, cada item deve ser um substantivo ou uma frase que começa com um verbo.

## Notas e dicas

Mantenha notas e dicas em apenas um parágrafo. A necessidade de mais de um parágrafo indica a necessidade de reestruturar o conteúdo e incluí-lo no corpo do artigo.

## Uso de maiúsculas

Na dúvida, não use letras maiúsculas. Em cabeçalhos, use as letras maiúsculas como na norma culta. Use letra maiúscula nos substantivos próprios e na primeira palavra após os dois pontos.

## Elementos da interface

* Tudo o que o usuário clicar será colocado em **negrito**. Por exemplo, &quot;Clique em **Continuar**.&quot; Valores de opção e mensagens de erro são formatados com _itálico_.
* Sempre que possível, evite mencionar o tipo de elemento da interface do usuário nas instruções. (Clique em **Avançar**. vs Clique no botão **Avançar**.)
* Use &quot;Choose&quot; e &quot;>&quot; em sequências de comando. (Escolha **Editar** > **Preferências**. vs Clique em Editar | Preferências.)
* Preposição: &quot;in&quot; para caixa de diálogo, janela, são um, painel, visualização, assistente, lista, pasta, nó.
* Preposição: &quot;ativada&quot; para tela, página, barra de ferramentas, barra de menu, guia, painel, faixa de opções.
* Preposição: Clique (Clique em **Próximo** vs. Clique em **Próximo**).

## Nomes de arquivos

Nomes de arquivos e pastas são formatados como código. Exemplo: o diretório de sistema `/var/log` contém logs para todos os ambientes.


## Números

Acima de tudo, regras de consistência ao abordar o problema dos números anotados em relação aos numerais.

Soletre um número, como &quot;cinco&quot; ou &quot;nove&quot; quando o número estiver abaixo de 10 (números de um a nove).

Escreva um número como um numeral, como &quot;42&quot; ou &quot;11&quot; quando:

* O número está acima de 9 (números dez e acima).
* Você está especificando o número:
   * Em uma linha de código ou trecho de código.
   * Em um caminho de arquivo ou nome de diretório.
   * Ao comunicar um intervalo, como &quot;entre 5 e 25&quot; ou &quot;números de revisão de 8 a 21&quot;.
   * Os números foram medidos ou calculados como &quot;62 paicas&quot; ou &quot;830 MHz&quot;.

Use uma mistura de números e numerais ao anotar uma quantidade de coisas numeradas, como &quot;uma coleção de quinze execuções de 1000 tentativas&quot;.

Escreva ambos os números em palavras ou ambos em numerais, se você tiver dois números em uma frase, um abaixo de 10 (como 4) e um acima de 10 (como 14). Por exemplo, você manteria os numerais aqui: &quot;14 minutos para cada 4 litros de fluido&quot;.


## Casos particulares de redação

<table class="relative-table" style="width: 100.0%;"><colgroup><col style="width: 12.003596%;"> <col style="width: 16.444849%;"> <col style="width: 71.55351%;"></colgroup>

<tbody>

<tr>

<th>Incorreto</th>

<th>Correto</th>

<th> Raciocínio
</th>

</tr>

<tr>

<td>Faça login na página da conta do Magento.com </td>

<td>Faça logon em sua conta da Adobe Commerce</td>

<td colspan="1">
</td>

</tr>

<tr>

<td>Extensões de terceiros (módulos)</td>

<td>extensões de terceiros (módulos)</td>

<td colspan="1">
</td>

</tr>

<tr>

<td>Trechos de código SQL</td>

<td>As instruções estão em maiúsculas (SELECT vs select)</td>

<td colspan="1">Melhor legibilidade</td>

</tr>

<tr>

<td colspan="1">

Referências a outros recursos.

Exemplo: consulte xyz na documentação do desenvolvedor


</td>

<td colspan="1">Consulte xyz na documentação do desenvolvedor</td>

<td colspan="1">

Requisito de acessibilidade: todos os links descrevem o destino do link.


</td>

</tr>

<tr>

<td colspan="1">

Adobe Commerce v2.4.0

Adobe Commerce 2.4.0

Adobe Commerce versão 2.4.0

</td>

<td colspan="1">Adobe Commerce 2.4.0 (sem v. ou versão)</td>

<td colspan="1"></td>

</tr>

<tr>

<td colspan="1">

2.4.x

2.4.X

</td>

<td colspan="1">

2.4.0

2.4.x

</td>

<td colspan="1">

Não há motivo para maiúsculas.

</td>

</tr>

<tr>

<td colspan="1">

Mensagem de erro: _&quot;Algo deu errado.&quot;_

Mensagem de erro: __Algo deu errado.__

</td>

<td colspan="1"> Mensagem de erro: <i>Algo deu errado.</i> </td>

<td colspan="1">
</td>

</tr>

</tbody>

</table>

## Acessibilidade

* Todos os elementos gráficos ou não textuais têm equivalentes textuais ou Texto Alt. Exemplo: ![exemplo_imagem](/url "alt_texto_para_esta_imagem").

* Todos os links descrevem seu destino. Exemplo [link](/uri "target_of_the_link").


<!--
## Accessible tables

Use tables for information that is best presented along two axes (rows and columns). Do not use tables when a list or definition list serves the purpose. If using tables, follow these recommendations:

*   Headers for rows and columns; row headers easier for screen readers.

*   Simple linear construction.

*   Content within cells consistently structured.  -->


## Linguagem abusiva

* Evite linguagem abusiva. 
* Evite linguagem racista ou &quot;pode parecer racista&quot;.
* Evite linguagem com fortes conotações negativas ou forte coloração emocional, como &quot;matar&quot;, &quot;terminar&quot;.


## Links 

A maioria dos links é exibida em listas de links dentro do artigo. Evite links integrados desnecessários.

A prática recomendada é isolar links em linha em uma lista de links com um título configurável.

Uma lista de links especializada, chamada de lista &quot;consulte também&quot;, é exibida somente no final de um artigo.    Use listas de links estrategicamente, não mais do que o necessário. Como regra geral, não mais do que seis links em uma lista de links.

### Links para sites externos

Use URLs comuns em vez de goURLs para vincular a páginas fora do [Adobe.com](http://Adobe.com).


## Vírgulas

Em geral, siga as recomendações do Manual de estilo de Chicago para pontuação de estilo aberto, pontuando somente quando necessário para evitar leituras incorretas. Por exemplo, você pode omitir a vírgula antes de uma conjunção em uma sentença composta se houver pouco ou nenhum risco de erro de leitura. Use a vírgula quando necessário para obter esclarecimentos.

* Sempre use a vírgula serial (uma vírgula precedente a _and_ ou _or_ em uma lista de três ou mais itens): x, y e z

* Coloque uma vírgula antes de uma conjunção introduzindo uma cláusula independente: &quot;Especifique um local e digite um nome para a lista de arquivos.&quot;

* Não separe as diferenças de plataforma com uma vírgula: &quot;... Ctrl (Windows) ou Command (Mac OS)&quot;

* Sempre use uma vírgula após uma frase ou cláusula introdutória: &quot;No Photoshop, importe o arquivo Illustrator.&quot;

## Versões

* Usamos &quot;version&quot; para todas as versões (principal/secundária/patch). Por exemplo, &quot;Versões compatíveis: Adobe Commerce 2.3.x&quot;

* Usamos &quot;x&quot; minúsculo ao escrever sobre todas as versões de patch em versões secundárias e todas secundárias com versões principais. Por exemplo, Adobe Commerce 2.x.x.

## Marcas

* O Magento Commerce agora é Adobe Commerce. Consulte o wiki [Termos de remarca](https://github.com/magento/knowledge-base/wiki) para obter mais informações sobre como usar um idioma de marca atualizado.
