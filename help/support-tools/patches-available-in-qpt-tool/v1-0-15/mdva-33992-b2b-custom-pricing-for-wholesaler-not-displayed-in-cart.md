---
title: "MDVA-33992: preço personalizado B2B para atacadista não exibido no carrinho"
description: O patch MDVA-33992 corrige o problema em que os preços personalizados para um cliente B2B não são refletidos quando um produto é adicionado a um carrinho. Este patch está disponível quando a Ferramenta de correções de qualidade (QPT) 1.0.15 está instalada. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.3.
exl-id: 6018fae6-762c-46c6-9497-ecf090115b7f
feature: B2B, Catalog Management, Orders, Shopping Cart
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 0%

---

# MDVA-33992: Preço personalizado B2B para atacadista não exibido no carrinho

O patch MDVA-33992 corrige o problema em que os preços personalizados para um cliente B2B não são refletidos quando um produto é adicionado a um carrinho. Este patch está disponível quando a Ferramenta de correções de qualidade (QPT) 1.0.15 está instalada. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.3.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:** Adobe Commerce na infraestrutura em nuvem 2.4.1 com B2B

**Compatível com as versões do Adobe Commerce:** Adobe Commerce na infraestrutura em nuvem e Adobe Commerce no local 2.3.0-2.4.1-p1 com B2B

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os preços personalizados para um cliente B2B não são refletidos quando um produto é adicionado ao carrinho.

<u>Etapas a serem reproduzidas</u>:

O problema pode ser reproduzido para a versão B2B com o Catálogo compartilhado ativado.

1. Crie uma empresa B2B com um catálogo compartilhado personalizado atribuído.
1. Crie um produto no catálogo personalizado da empresa com um preço personalizado (nível de preço).
1. Como cliente B2B, verifique se o preço do produto personalizado é exibido no catálogo.
1. Como cliente B2B, adicione o produto ao carrinho.

<u>Resultado esperado</u>:

O preço correto é exibido no carrinho de compras e corresponde ao preço no catálogo.

<u>Resultado real</u>:

O preço personalizado desaparece e o preço normal do catálogo padrão é exibido.

## Aplicar o patch

Para aplicar patches individuais, use os seguintes links, dependendo do seu produto Adobe Commerce:

* Adobe Commerce ou Magento Open Source no local: [Guia de atualização de software > Aplicar patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatendimento de correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de patches de qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis na ferramenta QPT, consulte o [Correções disponíveis na ferramenta QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) seção.
