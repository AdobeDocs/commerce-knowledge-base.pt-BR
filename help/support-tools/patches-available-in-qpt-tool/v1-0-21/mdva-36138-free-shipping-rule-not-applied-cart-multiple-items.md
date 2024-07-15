---
title: "MDVA-36138: regra de envio gratuito não aplicada ao carrinho de vários itens"
description: O patch MDVA-36138 corrige o problema em que, quando há vários itens no carrinho, o SKU correspondente no Frete gratuito não está recebendo frete gratuito aplicado. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.21 está instalada. A ID do patch é MDVA-36138. Observe que o problema foi corrigido no Adobe Commerce 2.4.3.
exl-id: 74e25ca8-e4fa-47f4-ab95-561f70e05727
feature: Orders, Shipping/Delivery, Personalization, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '467'
ht-degree: 0%

---

# MDVA-36138: regra de envio gratuito não aplicada ao carrinho de vários itens

O patch MDVA-36138 corrige o problema em que, quando há vários itens no carrinho, o SKU correspondente no Frete gratuito não está recebendo frete gratuito aplicado. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.21 está instalada. A ID do patch é MDVA-36138. Observe que o problema foi corrigido no Adobe Commerce 2.4.3.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

Adobe Commerce na infraestrutura em nuvem 2.3.4

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.3.2 e superior

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Se uma regra de frete gratuito for aplicada apenas a itens específicos, o desconto não se aplicará quando houver outros itens no carrinho.

<u>Etapas a serem reproduzidas</u>:

1. Crie produtos simples - simple1 e simple2.
1. Configurar o USPS (ou qualquer método de envio online):

   * Métodos permitidos: Priority Mail (um método selecionado para não ter uma longa lista de métodos no carrinho e na finalização).
   * Método gratuito: correspondência prioritária.

1. Criar uma regra de carrinho de compras:

   * Especificar código de cupom
   * Guia Condições: deixe em branco
   * Guia Ações:

   `Condition: SKU is simple1`
   `Free Shipping: For matching items only`

1. Adicione simple1 ao carrinho.
1. Aplique o código do cupom.
1. Adicione simple2 ao carrinho.

<u>Resultados esperados</u>:

* simple1 - deve ter frete grátis.
* simple2 - o frete deve ser pago.

<u>Resultados reais</u>:

O preço de envio inclui simple1 e simple2.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.
