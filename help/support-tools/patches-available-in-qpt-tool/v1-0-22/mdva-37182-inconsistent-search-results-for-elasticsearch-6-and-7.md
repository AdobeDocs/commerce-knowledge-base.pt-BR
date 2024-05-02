---
title: "MDVA-37182: resultados de pesquisa inconsistentes no Elasticsearch 6 e 7"
description: O patch MDVA-37182 corrige o problema de comportamento de pesquisa inconsistente nas versões 6 e 7 do Elasticsearch. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.22 está instalada. A ID do patch é MDVA-37182. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.3.
exl-id: 6c4e2d2f-cced-487d-b253-fd0c80bc6067
feature: Search, Services
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---

# MDVA-37182: resultados de pesquisa inconsistentes no Elasticsearch 6 e 7

O patch MDVA-37182 corrige o problema de comportamento de pesquisa inconsistente nas versões 6 e 7 do Elasticsearch. Este patch está disponível quando a variável [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.0.22 está instalado. A ID do patch é MDVA-37182. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.3.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:** Adobe Commerce na infraestrutura em nuvem 2.4.1

**Compatível com as versões do Adobe Commerce:** Adobe Commerce no local e Adobe Commerce na infraestrutura em nuvem 2.4.1-2.4.2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Comportamento de pesquisa inconsistente.

<u>Etapas a serem reproduzidas</u>:

1. Crie produtos com os seguintes detalhes:
   * Nomes: &quot;5127AC&quot;, &quot;5127SS&quot;, &quot;5127AB&quot;
   * SKUs: &quot;product1&quot;, &quot;product2&quot;, &quot;product3&quot;
1. Defina o mecanismo de pesquisa como Elasticsearch 6 (ES6).
1. Executar reindexação completa.
1. Na loja, pesquise por &quot;5127s&quot;.
1. Defina o mecanismo de pesquisa como Elasticsearch 7 (ES7).
1. Executar reindexação completa.
1. Na loja, pesquise por &quot;5127s&quot;.

<u>Resultado real:</u>:

ES6: a pesquisa não retorna resultados. ES7: a pesquisa retorna três produtos.

<u>Resultado esperado:</u>:

A pesquisa retorna um produto para ambas as versões.

## Aplicar o patch

Para aplicar patches individuais, use os seguintes links, dependendo do seu produto Adobe Commerce:

* Adobe Commerce ou Magento Open Source no local: [Guia de atualização de software > Aplicar patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatendimento de correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de patches de qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis na ferramenta QPT, consulte o [Correções disponíveis na ferramenta QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) seção.
