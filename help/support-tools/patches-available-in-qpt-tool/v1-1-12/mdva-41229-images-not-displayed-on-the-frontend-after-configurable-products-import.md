---
title: 'MDVA-41229: Imagens disponíveis no back-end não exibidas no front-end após a importação de produtos configuráveis'
description: O patch MDVA-41229 resolve o problema em que as imagens disponíveis no back-end não são exibidas no front-end após a importação de produtos configuráveis. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 está instalada. A ID do patch é MDVA-41229. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.
exl-id: 69d7374f-9f8b-4ec4-8a7f-135ee06135a3
feature: Data Import/Export, Configuration, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '688'
ht-degree: 2%

---

# MDVA-41229: Imagens disponíveis no back-end não exibidas no front-end após a importação de produtos configuráveis

O patch MDVA-41229 resolve o problema em que as imagens disponíveis no back-end não são exibidas no front-end após a importação de produtos configuráveis. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 está instalada. A ID do patch é MDVA-41229. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.2-p2 e 2.4.3-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

As imagens disponíveis no back-end não são exibidas no front-end após a importação configurável dos produtos.

<u>Etapas a serem reproduzidas</u>:

1. Instale um Adobe Commerce limpo.
1. Adicione um atributo personalizado indo para **Lojas** > **Atributos** > **Produto** > **Adicionar Novo Atributo** com as configurações abaixo:

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

1. Adicione este atributo ao Conjunto de Atributos Padrão dentro do Grupo de Detalhes do Produto (**Lojas** > **Atributos** > **Conjunto de Atributos**).
1. Baixe imagens definidas na pasta var dentro do diretório raiz do Adobe Commerce.
1. Vá para **Sistema** > **Transferência de Dados** > e importe o arquivo usando as opções abaixo:

   * Importar configurações:

      * Tipo de entidade: produtos

   * Comportamento de Importação:

      * Comportamento de Importação: Adicionar/Atualizar
      * Estratégia de validação: Parar se houver Erro
      * Contagem de Erros Permitidos: 1
      * Separador de campos: `;`
      * Separador de valores múltiplos: `,`
      * Constante de valor do atributo: EMPTYVALUE
      * Compartimento de campos: desmarcado

   * Arquivo a importar:

      * Selecione o arquivo para importar
      * Diretório do arquivo de imagens: deixe em branco

1. Vá para a loja na página `/product-set.html` e alterne entre diferentes Tamanhos de Conjunto. Para o Tamanho definido 24, não haverá galeria.

<u>Resultados esperados</u>:

A galeria de todos os produtos simples dentro de um produto configurável está visível com todas as imagens relacionadas.

<u>Resultados reais</u>:

Não há galeria para os produtos.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) na documentação do desenvolvedor.
