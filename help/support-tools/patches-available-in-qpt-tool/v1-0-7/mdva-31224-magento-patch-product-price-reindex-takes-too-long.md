---
title: "Patch MDVA-31224: a reindexação do preço do produto leva muito tempo"
description: O patch MDVA-31224 resolve o problema quando a reindexação do preço do produto leva muito tempo para ser concluída ou nunca é concluída. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) v.1.0.7 está instalada.
exl-id: 17f83fbf-9a43-4a65-b560-5f729b037c17
feature: Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 0%

---

# Correção do MDVA-31224: a reindexação do preço do produto leva muito tempo

O patch MDVA-31224 resolve o problema quando a reindexação do preço do produto leva muito tempo para ser concluída ou nunca é concluída. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) v.1.0.7 está instalada.

## Produtos e versões afetados

* O patch foi projetado para Adobe Commerce na infraestrutura em nuvem 2.3.3.
* O patch também é compatível com o Adobe Commerce no local e o Adobe Commerce na infraestrutura em nuvem 2.3.3 - 2.3.4-p2.

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A reindexação do preço do produto leva muito tempo para ser concluída ou nunca é concluída.

<u>Etapas a serem reproduzidas:</u>

1. Crie 6.000 produtos agrupados com 15 opções.
1. Crie 1 produto incluído com 30 opções.
1. Executar reindexação de preço da CLI:     `bin/magento indexer:reindex catalog_product_price`

<u>Resultados esperados:</u>

A reindexação do preço do produto leva 1,5 hora ou mais para ser concluída.

<u>Resultados reais:</u>

A reindexação do preço do produto leva pouco tempo (um ou dois minutos) para ser concluída.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.
