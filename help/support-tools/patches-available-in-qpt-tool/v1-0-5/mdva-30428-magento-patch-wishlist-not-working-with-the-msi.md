---
title: "MDVA-30428: lista de desejos não funciona com o Inventory management"
description: O patch MDVA-30428 resolve a lista de desejos que não funciona com o Inventory management (MSI). Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5 está instalada.
exl-id: 79e8d5d6-b073-48cf-8ecc-5c44667c12ad
feature: Inventory, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 0%

---

# MDVA-30428: lista de desejos não funciona com o Inventory management

O patch MDVA-30428 resolve a lista de desejos que não funciona com o Inventory management (MSI). Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5 está instalada.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.5-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.3 - 2.3.3-p1 (QPT 1.0.6) e 2.3.5 - 2.4.1 (QPT 1.0.5)

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Ao adicionar um produto à lista de desejos, quando o produto é atribuído a uma origem de estoque personalizada, a mensagem a seguir mostra &quot;*Não é possível adicionar o item à Lista de Desejos no momento: Não é possível adicionar produto sem estoque à lista de desejos.*&quot;

<u>Etapas a serem reproduzidas</u>:

1. Crie uma nova origem de inventário no Administrador do Commerce. Para ver as etapas, consulte [Catálogo > Adicionando uma nova Source](https://docs.magento.com/user-guide/catalog/inventory-sources-add.html?itm_source=merchdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=new%20inventory%20source) no guia do usuário.
1. Crie um novo inventário de estoque no Administrador do Commerce, atribua a nova fonte e o site padrão ao novo estoque. Para ver as etapas, consulte [Catálogo > Adicionando um novo estoque](https://docs.magento.com/user-guide/catalog/inventory-stock-add.html#add-new-stock) no guia do usuário.
1. Crie um produto simples e atribua o novo estoque somente como estoque.
1. Visite a página de detalhes do produto simples no front-end.
1. Adicione o produto à lista de desejos. O erro a seguir mostra: *Não é possível adicionar o item à Lista de Desejos no momento: Não é possível adicionar o produto sem estoque à lista de desejos*.

<u>Resultados esperados</u>:

O produto deve ser adicionado à lista de desejos com o estoque personalizado.

<u>Resultados reais</u>:

O produto não é adicionado à lista de desejos e uma mensagem de erro é exibida.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.
