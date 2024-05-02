---
title: "MDVA-30186: Opções de atributo não classificadas na resposta do GraphQL"
description: O patch MDVA-30186 resolve o problema em que as opções de atributo não são classificadas na resposta do GraphQL. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.23 está instalada. A ID do patch é MDVA-30186. Observe que o problema foi corrigido no Adobe Commerce 2.4.3.
exl-id: 7b2aef16-5012-4206-9444-e0b765f0c0c9
feature: Attributes, GraphQL, Categories
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# MDVA-30186: Opções de atributo não classificadas na resposta do GraphQL

O patch MDVA-30186 resolve o problema em que as opções de atributo não são classificadas na resposta do GraphQL. Este patch está disponível quando a variável [Ferramenta de correções de qualidade (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) O 1.0.23 está instalado. A ID do patch é MDVA-30186. Observe que o problema foi corrigido no Adobe Commerce 2.4.3.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce na infraestrutura em nuvem 2.3.4 e 2.4.2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.4 - 2.3.5-p2, 2.4.0 - 2.4.0-p1 e 2.4.2 - 2.4.2-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

<u>Etapas a serem reproduzidas</u>:

1. Adicione três opções ao atributo de cor existente.
1. Crie seis produtos simples com opções (Exemplo: *Opção 1*: 1 produto, *Opção 2*: 2 produtos, *Opção 3*: 3 produtos).
1. Crie uma categoria e atribua todos os produtos criados acima.
1. Agora faça a seguinte solicitação do GraphQL com a ID da categoria:

   <pre><code class="language-graphql">
    {
      products(
        filter: { category_id: { eq: "3" } }
        pageSize: 200
        currentPage: 1
        sort: { name: ASC }
      ) {
        aggregations {
          attribute_code
          count
          label
          options {
            count
            label
            value
          }
        }
        items {
          name
          sku
          url_key
        }
      }
    }
    </code></pre>

1. Agora, altere a ordem de classificação das opções de atributo na página de edição de atributos no Administrador.
1. Faça a solicitação GraphQL acima novamente e observe as opções de atributo de cor.

<u>Resultados esperados</u>:

As opções de atributo são classificadas de acordo com o pedido definido pelo Administrador.

<u>Resultados reais</u>:

As opções de atributo são sempre classificadas de acordo com o número associado de produtos.


## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de atualização de software > Aplicar patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatendimento de correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de patches de qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.
