---
title: '"Correção MDVA-31399: Subtotal (Incl. Imposto) na condição de regra do carrinho'
description: O patch MDVA-31399 adiciona o *Subtotal (Incl. Imposto)* opção para [condição de regra de preço do carrinho](https://docs.magento.com/user-guide/v2.3/marketing/price-rules-cart-create.html#step-2-describe-the-conditions), corrigindo o problema em que era impossível aplicar uma regra de preço do carrinho com base em Subtotal (Incl. Imposto) número. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12 está instalada.
exl-id: ea0f4060-753a-4b0d-896b-fff54ffd1a82
feature: Marketing Tools, Orders, Shopping Cart, Taxes
role: Admin
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 0%

---

# Correção MDVA-31399: Subtotal (Incl. Imposto) na condição de regra do carrinho

O patch MDVA-31399 adiciona o *Subtotal (Incluído Imposto)* opção para [condição de regra de preço do carrinho](https://docs.magento.com/user-guide/v2.3/marketing/price-rules-cart-create.html#step-2-describe-the-conditions), corrigindo o problema em que era impossível aplicar uma regra de preço do carrinho com base em Subtotal (Incl. Imposto) número. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12 está instalada.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

Adobe Commerce na infraestrutura em nuvem 2.3.5-p2

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce na infraestrutura em nuvem e Adobe Commerce no local 2.3.2 - 2.4.1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

É impossível aplicar uma regra de preço do carrinho com base em Subtotal (Incl. Imposto) número.

<u>Etapas a serem reproduzidas</u>:

1. Configure o preço do produto para incluir imposto.
1. Crie uma regra de imposto e uma alíquota de imposto para 20%.
1. Crie um produto com **Preço** = *100* (esse preço inclui imposto).
1. Crie uma nova regra de preço do carrinho com um cupom &quot;10off&quot; para aplicar desconto fixo de USD$ 10 se o subtotal corresponder a estas condições:

**Condições**: *Se TODAS essas condições forem VERDADEIRAS:*        * **Subtotal** igual ou maior que 100.*

<u>Resultados esperados</u>:

Há a capacidade de criar uma regra de preço do carrinho de subtotal com cupom para aplicar desconto ao subtotal, incluindo imposto.

<u>Resultados reais</u>:

Há duas opções nas condições de regra do carrinho: *Subtotal* e *Subtotal (Excl. Imposto)*, e qualquer um que seja selecionado, a regra é aplicada somente ao subtotal excluindo o imposto.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte os [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.
