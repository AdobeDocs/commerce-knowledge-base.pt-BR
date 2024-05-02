---
title: A pesquisa de SKU MDVA-28357 na página Pesquisa avançada não funciona
description: O MDVA-28357 resolve o problema em que a pesquisa por um SKU de produto na página Pesquisa avançada não resulta na exibição do produto relevante nos resultados da pesquisa. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.8 está instalada. Observe que o problema foi corrigido no Adobe Commerce versão 2.4.1.
exl-id: a89409b0-3155-4fac-9842-0d129dacd6e1
feature: Search
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---

# A pesquisa de SKU MDVA-28357 na página Pesquisa avançada não funciona

O MDVA-28357 resolve o problema em que a pesquisa por um SKU de produto na página Pesquisa avançada não resulta na exibição do produto relevante nos resultados da pesquisa. Este patch está disponível quando a variável [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O v.1.0.8 está instalado. Observe que o problema foi corrigido no Adobe Commerce versão 2.4.1.

## Produtos e versões afetados

* Este patch foi projetado para o Adobe Commerce no local 2.3.4-p2.
* O patch também é compatível com o Adobe Commerce no local e o Adobe Commerce na infraestrutura em nuvem 2.3.0 a 2.3.5-p2 e 2.4.0 a 2.4.0-p1.

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Na pesquisa avançada, pesquisar usando uma SKU consulta o campo SKU usando um curinga. Mas um curinga só pode ser usado com `sku.keyword`, portanto, isso não retornará o produto esperado.

<u>Etapas a serem reproduzidas</u>

1. Vá para a página Pesquisa avançada.
1. Pesquise por um número SKU.

<u>Resultado real</u>

Uma mensagem de erro é exibida: *Não foi possível encontrar nenhum item que corresponda a estes critérios de pesquisa. Modificar sua pesquisa*.

<u>Resultado esperado</u>

Um item de produto é exibido com uma mensagem: *Um item foi encontrado usando os seguintes critérios de pesquisa*  *SKU: XX-XXXX*

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Aplicar patches usando a Ferramenta de correções de qualidade](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatendimento de correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de patches de qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Para obter informações sobre outros patches disponíveis na ferramenta QPT, consulte o [Correções disponíveis na ferramenta QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) seção.
