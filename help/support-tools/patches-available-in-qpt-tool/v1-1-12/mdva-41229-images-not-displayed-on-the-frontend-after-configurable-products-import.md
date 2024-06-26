---
title: "MDVA-41229: imagens disponíveis no back-end não exibidas no front-end após a importação de produtos configuráveis"
description: O patch MDVA-41229 resolve o problema em que as imagens disponíveis no back-end não são exibidas no front-end após a importação de produtos configuráveis. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 está instalada. A ID do patch é MDVA-41229. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.
exl-id: 69d7374f-9f8b-4ec4-8a7f-135ee06135a3
feature: Data Import/Export, Configuration, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '688'
ht-degree: 2%

---

# MDVA-41229: Imagens disponíveis no back-end não exibidas no front-end após a importação de produtos configuráveis

O patch MDVA-41229 resolve o problema em que as imagens disponíveis no back-end não são exibidas no front-end após a importação de produtos configuráveis. Este patch está disponível quando a variável [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.12 está instalado. A ID do patch é MDVA-41229. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.2-p2 e 2.4.3-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

As imagens disponíveis no back-end não são exibidas no front-end após a importação configurável dos produtos.

<u>Etapas a serem reproduzidas</u>:

1. Instale um Adobe Commerce limpo.
1. Adicione um atributo personalizado acessando **Lojas** > **Atributos** > **Produto** > **Adicionar novo atributo** com as configurações abaixo:
   * Propriedades:
      * Propriedades do atributo:
         * Rótulo padrão: definir tamanho
         * Tipo de Entrada de Catálogo para Proprietário da Loja: Amostra de Texto
         * Valores Obrigatórios: Não
         * Atualizar imagem de visualização do produto: Sim
      * Gerenciar amostra (valores do seu atributo):

        | É padrão | Amostra do administrador | Descrição do administrador | Amostra de exibição de loja padrão | Descrição da exibição da loja padrão |
        |---|---|---|---|---|
        | não | 4 | 4 | 4 | 4 |
        | não | 24 | 24 | 24 | 24 |
        | não | 30 | 30 | 30 | 30 |
        | não | 60 | 60 | 60 | 60 |
        | não | 68 | 68 | 68 | 68 |
      * Propriedades avançadas de atributo:
         * Código do atributo: set_size
         * Escopo: Global
         * Valor Único: Não
         * Validação de Entrada para Proprietário da Loja: Nenhuma
         * Adicionar às Opções de Coluna: Não
         * Usar nas Opções de Filtro: Não
   * Gerenciar rótulos:
      * Gerenciar títulos (tamanho, cor etc.)
         * Visualização de armazenamento padrão: definir tamanho
   * Propriedades da vitrine:
      * Usar na pesquisa: Sim
      * Peso da pesquisa: 1
      * Visível na Pesquisa Avançada: Não
      * Comparável na loja: sim
      * Uso na navegação em camadas: filtrável (com resultados)
      * Usar na Navegação em Camadas dos Resultados da Pesquisa: Sim
      * Usar para Condições de Regra Promocional: Não
      * Visível nas Páginas do Catálogo na Loja: Sim
      * Usado na Lista de Produtos: Sim
      * Usado para Classificação na Lista de Produtos: Não
1. Adicionar este atributo ao Conjunto de atributos padrão dentro do Grupo de detalhes do produto (**Lojas** > **Atributos** > **Conjunto de atributos**).
1. Baixe imagens definidas na pasta var dentro do diretório raiz do Adobe Commerce.
1. Ir para **Sistema** > **Transferência de dados** > e importe o arquivo usando as opções abaixo:
   * Importar configurações:
      * Tipo de entidade: produtos
   * Comportamento de Importação:
      * Comportamento de Importação: Adicionar/Atualizar
      * Estratégia de validação: Parar se houver Erro
      * Contagem de Erros Permitidos: 1
      * Separador de campo: `;`
      * Separador de valores múltiplos: `,`
      * Constante de valor do atributo: EMPTYVALUE
      * Compartimento de campos: desmarcado
   * Arquivo a importar:
      * Selecione o arquivo para importar
      * Diretório do arquivo de imagens: deixe em branco
1. Ir para a loja para `/product-set.html` e alternar entre diferentes Tamanhos de conjunto. Para o Tamanho definido 24, não haverá galeria.

<u>Resultados esperados</u>:

A galeria de todos os produtos simples dentro de um produto configurável está visível com todas as imagens relacionadas.

<u>Resultados reais</u>:

Não há galeria para os produtos.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de atualização de software > Aplicar patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatendimento de correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de patches de qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.
