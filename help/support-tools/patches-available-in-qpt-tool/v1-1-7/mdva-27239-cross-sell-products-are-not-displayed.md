---
title: 'MDVA-27239: os produtos de venda cruzada não são exibidos'
description: O patch do MDVA-27239 corrige o problema em que os produtos de venda cruzada não são exibidos. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.7 está instalada. Observe que o problema foi corrigido no Adobe Commerce 2.3.6.
exl-id: a0392a07-645d-4811-8547-2c67e20b6313
feature: Products
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---

# MDVA-27239: os produtos de venda cruzada não são exibidos

O patch do MDVA-27239 corrige o problema em que os produtos de venda cruzada não são exibidos. Este patch está disponível quando a variável [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.7 está instalado. Observe que o problema foi corrigido no Adobe Commerce 2.3.6.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.3.4, 2.4.0

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.3.0 - 2.3.5-p2, 2.4.0 - 2.4.0-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os produtos de venda cruzada não são exibidos no bloco de venda cruzada na página do carrinho de compras.

<u>Pré-requisitos</u>:

1. Desative o módulo Magento_TargetRule ou remova-o do bloco de layout Magento\TargetRule\Block\Checkout\Cart\Crosssell.
1. Criar produto 1.
1. Crie uma atualização de programação para o Produto 1, de modo que os produtos recém-criados tenham row_id diferente de entity_id.
1. Crie o Produto 2, Produto 3 e Produto 4.
1. Defina o Produto 3 como venda cruzada para o Produto 4.
1. Defina o Produto 4 como venda cruzada para o Produto 2.

<u>Etapas a serem reproduzidas</u>:

1. Adicione o Produto 4 e o Produto 2 ao carrinho de compras.
1. Verifique a página do carrinho de compras.

<u>Resultados esperados</u>:

O produto 3 é exibido no bloco de venda cruzada.

<u>Resultados reais</u>:

O bloco de venda cruzada está vazio.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de atualização de software > Aplicar patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatendimento de correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de patches de qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.
