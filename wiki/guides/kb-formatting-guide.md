---
source-git-commit: c587986edc925c49bf95ab935888b59f265371af
workflow-type: tm+mt
source-wordcount: '574'
ht-degree: 0%

---
# Guia de Formatação KB

## Autor no Markdown

Geralmente, usamos o [Guia de estilo da sintaxe do Adobe Experience League Markdown](https://experienceleague.adobe.com/docs/authoring-guide-exl/using/markdown/syntax-style-guide.html?lang=en), mas há algumas diferenças e exceções. Além disso, certas tags HTML são necessárias em determinados casos.

A seguir estão exemplos da formatação do Markdown usada com mais frequência em nosso repositório.

## Formatação básica

Para formatar o texto como negrito, coloque-o entre dois asteriscos:

`This will be **bold** text`

Para formatar o texto como itálico, use um único asterisco:

`This text will be *italics*`

Para formatar o texto como sublinhado, use a marca `<ins>`:

`<ins>This text will be underlined</ins>`

Para adicionar uma quebra de linha, use a tag HTML `<br>`.


## Cabeçalhos

Use a formatação a seguir para cabeçalhos de H2 a H5. H1 nunca é usado, pois o título do artigo é considerado H1.

`## Header 2 `

`### Header 3 `

`#### Header 4`

`##### Header 5`

## Código em linha e blocos

Use acentos graves únicos para delimitar o elemento de código que você deseja realçar:

Isso é \`código em linha\` em um parágrafo de texto.

### Blocos de código

Para inserir um bloco de código, coloque o bloco de código entre três acentos graves e especifique o idioma depois de abrir os acentos graves triplos:

\`\`\` sql

SELECIONAR TABLE_NAME COMO `Table`,
ROUND((DATA_LENGTH + INDEX_LENGTH) / 1024 / 1024) COMO `Size (MB)`
DE information_schema.TABLES
ONDE TABLE_SCHEMA = &quot;%project_id%&quot;
ORDENAR POR (DATA_LENGTH + INDEX_LENGTH) DESC;

\`\`\`

Isso será renderizado como:

```sql
SELECT TABLE_NAME AS `Table`,
  ROUND((DATA_LENGTH + INDEX_LENGTH) / 1024 / 1024) AS `Size (MB)`
FROM information_schema.TABLES
WHERE TABLE_SCHEMA = "%project_id%"
ORDER BY (DATA_LENGTH + INDEX_LENGTH) DESC;
```

De acordo com nossas regras de impressão, você sempre precisa especificar um idioma para o bloco de código.

Para obter a lista de idiomas compatíveis, consulte https://github.com/github/linguist/blob/master/lib/linguist/languages.yml.

Se o realce não funcionar para um determinado idioma no Markdown (ou seja, o idioma não é compatível), para torná-lo pelo menos destacado quando publicado em https://support.magento.com/hc/en-us/, use a seguinte HTML:

```html
<pre><code class="language-%language-code%"
your code here
</pre></code>
```

Onde ``%language-code%`` são os códigos definidos por [Linguagens com suporte para Prism.js](https://prismjs.com/#supported-languages).

## Listas

Sempre separe listas do restante do conteúdo por linhas em branco. As listas devem ser precedidas e seguidas por uma linha em branco.

Use a seguinte formatação para listas ordenadas:

```markdown
1. First numbered list item.
1. Second numbered list item.
...
1. Last numbered list item.
```

Para criar uma lista com marcadores não ordenada, comece uma linha com *, ou +, ou -. Mas selecione um método e use-o de forma consistente em todo o artigo.

Exemplo:

```markdown
* Unordered list item.
* Unordered list item.
---
* Last unordered list item.
```

Para adicionar conteúdo entre itens de lista, adicione 4 espaços no início da linha:

```markdown
* List item.
* List item.
    Here's some content between list items.
* Here we continue the list
```

Também é possível incorporar listas desse modo.

## Links

Os links externos são diretos:

```markdown
[Adobe](https://www.adobe.com)
```

### Links para anexos

Qualquer tipo de anexo deve estar nos formatos .png, .jpg e .jpeg. Para fins de segurança, só aceitamos anexos que estejam em um dos três formatos.

Para inserir uma imagem, coloque a imagem na subpasta *assets* na mesma pasta de seção do artigo e use a seguinte sintaxe para inserir a imagem no seu artigo:

```markdown
![alt text](assets/image.png)
```

Se você quiser personalizar o tamanho da imagem, será necessário fazer isso usando a seguinte tag HTML:

```html
<img src = "assets/image.png" alt = "your alt text" width="custom width, ex: 250px">
```

```markdown
[asset_title](assets/%file_name%).
```

### Links para seções específicas no artigo

Se você precisar referenciar uma seção dentro do seu artigo, não será necessário criar uma âncora separada. Eles são gerados automaticamente no momento da publicação para todos os cabeçalhos H2-H6. As âncoras são geradas a partir do cabeçalho, tornando todas as palavras em minúsculas e usando &quot;-&quot; para separar palavras.

Exemplo:

```markdown
## This is header
```

Este é um link para este cabeçalho:

```markdown
[this is link to the anchor in the same article](#this-is-header)
```

Se você precisar referenciar um elemento diferente do cabeçalho, use HTML para definir o elemento a ser adicionado, use o [atributo id](https://www.w3schools.com/html/html_id.asp). Em seguida, você pode usar o Markdown ou o HTML para fazer referência a essa ID.

### Links e links relativos a outros artigos

Não use links relativos para fazer referência a nossos artigos da knowledge base de suporte. Esses links não funcionarão quando o seu artigo for publicado na [Central de Ajuda da Adobe Commerce](https://support.magento.com/hc/en-us).
Use os hiperlinks completos da [Central de Ajuda da Adobe Commerce](https://support.magento.com/hc/en-us).


## Tabelas

Use a formatação [HTML para tabelas](https://www.w3schools.com/html/html_tables.asp).


## Avisos e blocos de informações

Bloco de nota de sucesso:

```
>![success]
>
>This is a success note
```

Bloco de aviso:

```
>![warning]
>
>This is a warning
```

Bloco de nota de informação:

```
>![info]
>
>This is a block with additional info
```
