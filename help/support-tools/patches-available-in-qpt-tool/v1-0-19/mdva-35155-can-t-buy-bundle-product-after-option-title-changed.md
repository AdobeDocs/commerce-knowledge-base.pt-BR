---
title: "MDVA-35155: Não é possível comprar o produto do pacote após a alteração do título da opção"
description: O patch MDVA-35155 resolve o problema em que um produto de pacote não pode ser comprado depois que o título da opção é alterado. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 está instalada. A ID do patch é MDVA-35155. Observe que o problema foi corrigido no Adobe Commerce versão 2.4.3.
exl-id: 79770c69-1bb0-48d8-acdf-c8c1272f9da8
feature: Products
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%

---

# MDVA-35155: Não é possível comprar o produto do pacote após a alteração do título da opção

O patch MDVA-35155 resolve o problema em que um produto de pacote não pode ser comprado depois que o título da opção é alterado. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 está instalada. A ID do patch é MDVA-35155. Observe que o problema foi corrigido no Adobe Commerce versão 2.4.3.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

Adobe Commerce na infraestrutura em nuvem 2.3.5

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce no local e Adobe Commerce na infraestrutura em nuvem 2.3.0-2.3.5-p2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os produtos do pacote não podem ser comprados depois que o título da opção é alterado.

<u>Etapas a serem reproduzidas</u>:

1. Crie um novo produto do pacote por meio de **Importação de Produto**.
1. O produto é normal tanto no Admin quanto no front-end (em estoque e pode ser adicionado ao carrinho).
1. Atualize o mesmo produto com alterações no nome em `bundle_values` e importe-o novamente.

<u>Resultados esperados</u>:

A opção de pacote existente é atualizada com o novo nome e mantém os mesmos itens nele.

<u>Resultados reais</u>:

* O administrador tenta mesclar produtos com o mesmo SKU em uma única seção de opção de pacote, resultando em uma seção de opção vazia.
* O produto está esgotado no front-end (mesmo após um reindex).

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte a seção [Patches disponíveis no QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).
