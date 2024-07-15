---
title: "Patch MDVA-31791: melhoria da página do produto com produtos relacionados e regras do target"
description: O patch MDVA-31791 melhora o desempenho das páginas do produto quando [Produtos relacionados](https://docs.magento.com/user-guide/catalog/settings-advanced-related-products.html) ou [Regras de produtos relacionados](https://docs.magento.com/user-guide/marketing/product-related-rules.html) (regras do target) são usados. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.9 está instalada. Observe que o problema foi corrigido no Adobe Commerce 2.4.1.
exl-id: e737bccb-d9eb-4794-9d6b-2c22fa8edaa2
feature: Marketing Tools, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 0%

---

# Correção do MDVA-31791: melhoria da página do produto com produtos relacionados e regras do Target

O patch MDVA-31791 melhora o desempenho das páginas de produtos quando [Produtos relacionados](https://docs.magento.com/user-guide/catalog/settings-advanced-related-products.html) ou [Regras de produtos relacionados](https://docs.magento.com/user-guide/marketing/product-related-rules.html) (regras de destino) são usadas. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.9 está instalada. Observe que o problema foi corrigido no Adobe Commerce 2.4.1.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

Adobe Commerce na infraestrutura em nuvem 2.4.0

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce na infraestrutura de nuvem e Adobe Commerce no local 2.3.4, 2.3.4-p1, 2.3.4-p2, 2.4.0, 2.4.0-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Baixo desempenho das páginas de produtos se os produtos relacionados ou as regras do Target forem usados.

Considere a aplicação do patch MDVA-31791 se você for usar a funcionalidade do [Produto relacionado](https://docs.magento.com/user-guide/catalog/settings-advanced-related-products.html) ou das [Regras de produto relacionado](https://docs.magento.com/user-guide/marketing/product-related-rules.html).

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte os [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.
