---
title: "Correção MDVA-33975: cálculos de preço do GraphQL"
description: "O patch MDVA-33975 corrige problemas de cálculo de preço do GraphQL. Esses problemas incluem:"
exl-id: a8266334-72cb-4b50-9ff5-9a977d762e5c
feature: GraphQL, Customer Service, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---

# Correção do MDVA-33975: cálculos de preço do GraphQL

O patch MDVA-33975 corrige problemas de cálculo de preço do GraphQL. Esses problemas incluem:

* Quando uma regra de preço de catálogo é aplicada a um determinado grupo de clientes, os preços dos itens no carrinho e o total do pedido não são calculados corretamente no GraphQL.
* As regras de preço de catálogo não estão incluídas em `CartItemPrices` na API.
* O preço de grupo do cliente geral não é adicionado na resposta de consulta de produto do GraphQL.
* Recalcular totais de cota antes de dar uma resposta sobre preços de cota causa a perda das regras aplicadas.
* O desconto do valor do frete não foi recuperado na última etapa de faturamento e o total geral foi exibido incorretamente.
* O desconto não é aplicado no GraphQL quando o segmento do cliente é usado na condição da regra de preço do carrinho.

Este patch está disponível quando a variável [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O v.1.0.14 está instalado.

## Produtos e versões afetados

* O patch foi projetado para o Adobe Commerce no local 2.4.1.
* O patch também é compatível com as seguintes versões do Adobe Commerce: Adobe Commerce no local e Adobe Commerce na infraestrutura em nuvem 2.3.4 - 2.4.1.

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Aplicar o patch

Para aplicar patches individuais, use os seguintes links, dependendo do seu produto Adobe Commerce:

* Adobe Commerce ou Magento Open Source no local: [Guia de atualização de software > Aplicar patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatendimento de correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de patches de qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis na ferramenta QPT, consulte o [Correções disponíveis na ferramenta QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) seção.
