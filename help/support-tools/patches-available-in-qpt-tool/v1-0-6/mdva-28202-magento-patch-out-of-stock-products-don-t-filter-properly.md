---
title: "Patch MDVA-28202: produtos esgotados não filtram corretamente"
description: O patch MDVA-28202 resolve o problema em que os produtos esgotados não são filtrados corretamente usando o filtro **Preço** em um front-end da loja da Adobe Commerce. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) v.1.0.6 está instalada.
exl-id: 45976602-15f3-4fef-9d90-da2b3fe6046d
feature: Catalog Management, Categories, Orders, Products
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# Correção do MDVA-28202: produtos esgotados não são filtrados corretamente

O patch MDVA-28202 resolve o problema em que os produtos sem estoque não são filtrados corretamente usando o filtro **Price** em um front-end de loja da Adobe Commerce. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) v.1.0.6 está instalada.

## Produtos e versões afetados

* O patch foi projetado para Adobe Commerce na infraestrutura em nuvem 2.3.5-p1.
* O patch também é compatível com o Adobe Commerce no local e o Adobe Commerce na infraestrutura em nuvem 2.3.4 - 2.4.1.

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Produtos sem estoque não filtram corretamente usando o filtro **Preço** no Administrador do Commerce.

<u>Pré-requisito:</u>

* Defina **Exibir Produtos sem Estoque** = &quot;*Sim*&quot; em **Lojas > Configuração > CATÁLOGO > Inventário > Opções de Estoque**.

<u>Etapas a serem reproduzidas:</u>

1. Crie um produto configurável com dois produtos simples (Exemplo: set **Price** = *$1500*).
1. Ambos os produtos simples devem estar &quot;esgotados&quot; ao criar o produto configurável.
1. Atribua este produto configurável a uma categoria.
1. Reindexe e verifique a tabela `catalog_product_index_price` usando a ID de entidade do produto configurável acima.
1. Salve todos os preços de produtos = *$0*.
1. Carregue a categoria e confirme a disponibilidade do produto.
1. Abra o filtro **Preço** da navegação em camadas.
1. Observe que o filtro **Preço** tem uma opção de &quot; *$0,00 - $9.99* &quot;.
1. Clique nesta opção de filtro acima de **Preço** e defina o **Preço** = *$1500*, e você obterá o produto configurável que criamos acima.

<u>Resultado esperado:</u>

O produto é filtrado dentro da faixa de preços correta, conforme esperado.

<u>Resultado real:</u>

O produto está sob um filtro de intervalo de preços incorreto.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Aplique patches usando a Ferramenta de patches de qualidade](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Para obter informações sobre outros patches disponíveis na ferramenta QPT, consulte a seção [Patches disponíveis na ferramenta QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).

Para saber mais sobre produtos configuráveis, consulte este artigo em nossa documentação para desenvolvedores: [Crie um tutorial de produto configurável](https://devdocs.magento.com/guides/v2.4/rest/tutorials/configurable-product/config-product-intro.html) em nossa documentação para desenvolvedores.
