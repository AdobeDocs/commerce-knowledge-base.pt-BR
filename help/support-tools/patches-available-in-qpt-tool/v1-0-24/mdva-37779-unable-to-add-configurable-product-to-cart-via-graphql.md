---
title: "MDVA-37779: Não é possível adicionar o produto configurável ao carrinho por meio do GraphQL"
description: O patch do Adobe Commerce MDVA-37779 resolve o problema de como é impossível adicionar um produto configurável ao carrinho quando a ID do site não é igual à ID da loja. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.24 está instalada. A ID do patch é MDVA-37779. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4. 
exl-id: 5f344896-39c3-4e17-89b8-1b987bae2968
feature: GraphQL, Configuration, Orders, Products, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 0%

---

# MDVA-37779: Não é possível adicionar o produto configurável ao carrinho via GraphQL

O patch do Adobe Commerce MDVA-37779 resolve o problema de como é impossível adicionar um produto configurável ao carrinho quando a ID do site não é igual à ID da loja. Este patch está disponível quando a variável [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.0.24 está instalado. A ID do patch é MDVA-37779. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

Adobe Commerce na infraestrutura em nuvem 2.4.2

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce no local e Adobe Commerce na infraestrutura em nuvem 2.4.2 - 2.4.2-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

É impossível adicionar o produto configurável ao carrinho quando a ID do site não é igual à ID da loja.

<u>Pré-requisitos</u>:

Ter uma segunda visualização de site, loja e loja em que a ID do site não é igual à ID da loja.

<u>Etapas a serem reproduzidas</u>:

1. Criar um carrinho vazio usando a mutação GraphQl `createEmptyCart`.
1. Tente adicionar um produto configurável ao carrinho usando o `addConfigurableProductsToCart` mutação.

<u>Resultados esperados</u>:

Produto adicionado ao carrinho.

<u>Resultados reais</u>:

Obter um erro: *Não foi possível adicionar o produto com o SKU xxxx ao carrinho de compras: o site com a ID 3 solicitada não foi encontrado. Verifique o site e tente novamente.*

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de atualização de software > Aplicar patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.


## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatendimento de correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de patches de qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis na ferramenta QPT, consulte o [Correções disponíveis na ferramenta QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) seção.
