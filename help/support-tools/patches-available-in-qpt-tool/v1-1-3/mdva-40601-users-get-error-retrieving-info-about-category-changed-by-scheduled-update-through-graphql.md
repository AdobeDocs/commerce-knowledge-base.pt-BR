---
title: "MDVA-40601: Não é possível recuperar dados sobre categoria alterada pela atualização agendada via GraphQL"
description: O patch de qualidade MDVA-40601 do Adobe Commerce corrige o problema em que os usuários recebem um erro ao obter informações sobre a categoria alterada por atualização agendada por meio do GraphQL. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.3 está instalada. A ID do patch é MDVA-40601. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.
exl-id: b1ea93e7-8d4a-4bdd-8267-cc60de25bd39
feature: Categories, GraphQL
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '434'
ht-degree: 0%

---

# MDVA-40601: Não é possível recuperar dados sobre categoria alterada pela atualização agendada via GraphQL

O patch de qualidade MDVA-40601 do Adobe Commerce corrige o problema em que os usuários recebem um erro ao obter informações sobre a categoria alterada por atualização agendada por meio do GraphQL. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.3 está instalada. A ID do patch é MDVA-40601. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.3.3 e 2.4.2

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.3.1 - 2.4.2-p2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os usuários recebem um erro ao tentar recuperar informações sobre a categoria alterada pela atualização agendada por meio do GraphQL.

<u>Etapas a serem reproduzidas</u>:

1. Configure uma estrutura de categoria com uma subcategoria conforme indicado abaixo:

   <pre>
   <code class="language-graphql">
   - Root
    - Some category
         - Some child category
   </code>
   </pre>

1. Execute a consulta do GraphQL com a ID 49 de &quot;Alguma categoria&quot;.

   <pre>
    <code class="language-graphql">
    query {
     category(id: 49) {
      name
      children {
        name
       }
     }
   }
   </code>
   </pre>

   Resultado:

   <pre>
    <code class="language-graphql">
    {
      "data": {
        "category": {
          "name": "Some category",
          "children": [
            {
              "name": "Some child category"
            }
          ]
        }
      }
    }
    </code>
    </pre>

1. Crie uma atualização de agendamento para &quot;Alguma categoria&quot; com um nome de categoria diferente.
1. Aguarde a atualização do cronograma ser ativada.
1. Execute a mesma query fornecida acima.

<u>Resultados esperados</u>:

Você recebe o mesmo resultado, mas com o nome de categoria atualizado.

<u>Resultados reais</u>:

Você recebe o seguinte erro:

<pre>
<code class="language-graphql">
{
  "errors": [
    {
      "debugMessage": "uasort() expects parameter 1 to be array, string given",
      "message": "Internal server error",
      "extensions": {
        "category": "internal"
      },
      "locations": [
        {
          "line": 2,
          "column": 3
        }
      ],
      "path": [
        "category"
      ]
    }
  ],
  "data": {
    "category": null
  }
}
</code>
</pre>

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do tipo de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre correções de qualidade para o Adobe Commerce, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Para obter informações sobre outros patches disponíveis no QPT, consulte a seção [Patches disponíveis no QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).
