---
title: A Base de conhecimento de suporte da Adobe Commerce começa a aceitar contribuições
description: A partir de 15 de junho, a equipe da Base de conhecimento de suporte da Adobe Commerce começará a aceitar edições diretas e novas contribuições de artigo da comunidade externa da Adobe Commerce por meio do repositório GitHub da [magento/knowledge-base](https://github.com/magento/knowledge-base).
exl-id: b5198de0-d6b5-4107-8b74-a12606583596
feature: Support
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '523'
ht-degree: 0%

---

# A Base de conhecimento de suporte da Adobe Commerce começa a aceitar contribuições

A partir de 15 de junho, a equipe da Base de conhecimento de suporte da Adobe Commerce começará a aceitar edições diretas e novas contribuições de artigos da comunidade externa da Adobe Commerce por meio do [magento/knowledge-base](https://github.com/magento/knowledge-base) Repositório do GitHub.

Ocorreu um erro de digitação em um de nossos artigos ou uma etapa de solução de problemas incompleta?
Agora você mesmo pode corrigir e obter pontos de contribuição!

## Contribute

Agradecemos todos os tipos de contribuições, desde pequenas correções de digitação até artigos completos de solução de problemas. A contribuição para esse repositório gera pontos de recompensa, semelhantes à contribuição para o código do Adobe Commerce e nossa documentação do desenvolvedor. Consulte [Pontos de premiação de contribuição](https://github.com/magento/knowledge-base/blob/main/docs/contribution-points.md) para obter detalhes.

### Fluxo de contribuição geral

1. Bifurque este repositório.
1. Faça edições no repositório bifurcado.
1. Envie uma solicitação de pull (PR) para este repositório.
1. Os testes são executados:
   * Adobe CLA - certificando-se de que o Contrato de licença de colaborador de código aberto do Adobe esteja assinado.
   * Teste de Markdown Linting - verificar se a sintaxe de Markdown está correta.
   * Teste de validação da estrutura de arquivos - verificando se a confirmação é feita de acordo com o [estrutura de arquivo necessária](https://github.com/magento/knowledge-base/blob/main/.github/CONTRIBUTING.md#file_structure).
1. Fluxo de aprovações de PR:
   1. Os autores da base de conhecimento (KB) de suporte revisam a PR dentro de um período de vários dias e adicionam rótulos.
   1. O gravador da base de conhecimento pode aprovar/negar/solicitar alterações.
   1. Se aprovado, o escritor da Base de conhecimento adiciona etiquetas correspondentes ao nível de entrada fornecido na PR e o SME (Internal Subject Matter Expert, especialista interno no assunto) analisa a PR.
   1. O SME pode aprovar/negar/solicitar alterações.
1. Quando todas as correções forem feitas (se houver alguma solicitada) e o gravador da base de conhecimento e o SME aprovarem a PR, o gravador da base de conhecimento importará conteúdo para o repositório interno e o mesclará internamente.
1. A variável [magento/knowledge-base](https://github.com/magento/knowledge-base) o repositório sincroniza com o interno em 20 minutos.
1. Depois que os repositórios são sincronizados, sua PR é fechada e você obtém [pontos de contribuição](#contribution-points).

Para obter detalhes sobre o fluxo de contribuição, consulte o [Guia do colaborador](https://github.com/magento/knowledge-base/blob/main/.github/CONTRIBUTING.md).
Para modelos, guia de estilo e diretrizes de formatação, consulte [Documentação](https://github.com/magento/knowledge-base/tree/main/docs).

### Encontre o arquivo de artigo da Base de conhecimento de suporte no Github

Na Base de conhecimento de suporte (KB), os artigos são organizados em seções, que se aninham em categorias.

Por exemplo, a variável [Como se inscrever para obter atualizações de status do Adobe Magento](/help/how-to/general/how-to-subscribe-to-adobe-magento-status-updates.md) Este artigo pertence à seção Geral na categoria Como.

É possível ver o nome da seção e da categoria no caminho da navegação estrutural na página do artigo. Consulte a imagem abaixo:

![navegação estrutural de categoria e seção](assets/breadcrumbs.png)

Os arquivos de artigo são organizados da mesma forma no [magento/knowledge-base](https://github.com/magento/knowledge-base) acordo de recompra
Todo o conteúdo é armazenado no `src` pasta, com pastas para categorias e pastas aninhadas para seções; os nomes dos arquivos coincidem com os títulos dos artigos ou são semelhantes.

Você também pode usar a pesquisa dentro do repositório usando um texto do artigo da Base de conhecimento de suporte como uma sequência de pesquisa. Quando a pesquisa retorna arquivos contendo essa string, certifique-se de escolher o arquivo que pertence à seção e categoria corretas.

### Pontos de contribuição

A variável [magento/knowledge-base](https://github.com/magento/knowledge-base) repo integrado ao Magento Community Engineering para obter pontos de contribuição e suporte.

Consulte [Pontos de contribuição](https://github.com/magento/knowledge-base/blob/main/docs/contribution-points.md) documento para ver como os pontos são recompensados.
