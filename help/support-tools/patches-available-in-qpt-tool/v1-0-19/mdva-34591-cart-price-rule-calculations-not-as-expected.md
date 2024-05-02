---
title: "MDVA-34591: cálculos de regra de preço do carrinho não conforme esperado"
description: O patch MDVA-34591 corrige o problema em que a regra de preço do carrinho com **Desconto de quantidade máxima aplicado a** não funciona corretamente se várias regras de preço do carrinho forem aplicadas. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 está instalada. A ID do patch é MDVA-34591. Observe que o problema está programado para ser corrigido no Adobe Commerce versão 2.4.3.
exl-id: 1fa196bb-aab1-4364-a1b0-7c31d6d27d6d
feature: Orders, Price Rules, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '547'
ht-degree: 0%

---

# MDVA-34591: cálculos de regra de preço do carrinho não conforme esperado

O patch MDVA-34591 corrige o problema em que a regra de preço do carrinho com **Desconto de Qtde Máxima Aplicado a** não funciona corretamente se várias regras de preço de carrinho forem aplicadas. Este patch está disponível quando a variável [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.0.19 está instalado. A ID do patch é MDVA-34591. Observe que o problema está programado para ser corrigido no Adobe Commerce versão 2.4.3.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

Adobe Commerce na infraestrutura em nuvem 2.3.6

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce no local e Adobe Commerce na infraestrutura em nuvem 2.3.0-2.4.2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

<u>Etapas a serem reproduzidas</u>:

1. Acesse o Administrador e crie as duas regras a seguir:

   * Regra 1: US$ 10 de desconto em no máximo três itens no carrinho. Definir prioridade = *3*.
   * Regra 2: 50% de desconto em todos os produtos do carrinho. Definir prioridade = *1*.

1. Vá para a loja.

1. Adicione oito quantidades de um conjunto de produtos ao preço = *$ 51* cada um ao carrinho.

1. Verifique o valor do desconto no carrinho.

<u>Resultados esperados</u>:

O desconto calculado correto é de US$ 234, conforme esperado.

* Cálculos:

  Regras de preço do carrinho de correspondência: Regra 2, Regra 1\
  Aplique a Regra 2 (50% de desconto), portanto, Desconto = US$ 204\
  Aplique a Regra 1 (10 de 3 itens), portanto, Desconto = US$ 30\
  Desconto total = MÍN ( 408/2 + 10x3, 8 &#42; 51) = MÍN. (204 + 30, 8 &#42; 51) = US$ 234

<u>Resultados reais</u>:

O desconto é calculado incorretamente como US$ 153, causado pela quantidade incorreta usada para calcular o valor de desconto máximo, já que o valor de desconto fixo é aplicado independentemente do valor dos produtos no carrinho de compras.

* Cálculos:

  Regras de preço do carrinho de correspondência: Regra 2, Regra 1\
  Aplique a Regra 2 (50% de desconto), portanto, Desconto = US$ 204\
  Aplique a Regra 1 (10 de 3 itens), portanto, Desconto = US$ 30\
  Desconto Total = MÍN (204 + 30, 3 &#42; 51) = US$ 153

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de atualização de software > Aplicar patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatendimento de correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de patches de qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte o [Patches disponíveis no QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) seção.
