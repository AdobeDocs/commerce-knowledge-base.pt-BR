---
title: "ACSD-45488: produto configurável com várias fontes não devolvidas ao estoque automaticamente"
description: O patch ACSD-45488 resolve o problema em que um produto configurável com várias fontes não é devolvido ao estoque automaticamente. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.18 está instalada. A ID do patch é ACSD-45488. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.
exl-id: 83332226-b14e-4d36-bf65-170f55fff270
feature: Configuration, Orders, Products, Returns
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 0%

---

# ACSD-45488: produto configurável com várias fontes que não são retornadas ao estoque automaticamente

O patch ACSD-45488 resolve o problema em que um produto configurável com várias fontes não é devolvido ao estoque automaticamente. Este patch está disponível quando a variável [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.18 está instalado. A ID do patch é ACSD-45488. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2 - 2.4.5

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Um produto configurável com várias fontes não é devolvido ao estoque automaticamente.

<u>Etapas a serem reproduzidas</u>:

1. Criar uma fonte de estoque secundária.
1. Crie um produto configurável com dois produtos virtuais associados.
1. Atribua os produtos associados à origem de estoque padrão e defina a quantidade como um.
1. Verifique a `stock_status` de `cataloginventory_stock_status`.
1. Defina ambos os produtos associados como *sem estoque*.
1. Verifique a `stock_status` de `cataloginventory_stock_status`.
1. Defina os dois produtos associados como *em estoque*.
1. Verifique a `stock_status` de `cataloginventory_stock_status`.

<u>Resultados esperados</u>:

O status do estoque do produto configurável é atualizado para *em estoque* quando os produtos associados estiverem definidos para serem colocados em estoque.

<u>Resultados reais</u>:

O status do estoque do produto configurável não é atualizado para *em estoque* quando os produtos associados estiverem definidos para serem colocados em estoque.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de atualização de software > Aplicar patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatendimento de correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de patches de qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.
