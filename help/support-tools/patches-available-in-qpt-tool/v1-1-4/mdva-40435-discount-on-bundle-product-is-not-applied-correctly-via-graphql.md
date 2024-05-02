---
title: "MDVA-40435: o desconto no produto do pacote não é aplicado corretamente por meio do GraphQL"
description: O patch MDVA-40435 resolve o problema em que o desconto em um produto empacotado não é aplicado corretamente pelo GraphQL. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.4 está instalada. A ID do patch é MDVA-40435. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.
exl-id: 939ba940-35b5-4ab0-81fe-38981246e389
feature: GraphQL, Orders, Personalization, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 0%

---

# MDVA-40435: Desconto no produto do pacote não é aplicado corretamente via GraphQL

O patch MDVA-40435 resolve o problema em que o desconto em um produto empacotado não é aplicado corretamente pelo GraphQL. Este patch está disponível quando a variável [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.4 está instalado. A ID do patch é MDVA-40435. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.4 - 2.4.3-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O desconto em um produto empacotado não é aplicado corretamente via GraphQL.

<u>Etapas a serem reproduzidas</u>:

1. Crie uma regra de preço do carrinho com um código de cupom para desconto fixo de US$ 5.
1. Crie um carrinho vazio via GraphQL.
1. Adicione um produto incluído ao carrinho por meio do GraphQL.
1. Aplique o código do cupom no valor fixo (5$) via GraphQL.
1. Obtenha as informações do carrinho por meio do GraphQL.

<u>Resultados esperados</u>:

&quot;descontos&quot; é de US$ 5.

<u>Resultados reais</u>:

&quot;descontos&quot; é NULL.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de atualização de software > Aplicar patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatendimento de correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de patches de qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte o [Patches disponíveis no QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) seção.
