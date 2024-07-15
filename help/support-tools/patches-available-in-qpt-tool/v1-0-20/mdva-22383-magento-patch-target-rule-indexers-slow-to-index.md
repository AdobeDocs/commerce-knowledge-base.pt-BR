---
title: "MDVA-22383: indexadores de regras de destino lentos para indexar"
description: O patch MDVA-22383 resolve o problema em que a reindexação dos indexadores Produto/Regra de destino e Regra de destino/Produto está demorando muito. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20 está instalada. A ID do patch é MDVA-22383. Observe que o problema foi corrigido no Adobe Commerce 2.3.5.
exl-id: fbf28983-5883-4769-90bd-1c97c2b2e2b8
source-git-commit: 975f5b5c95ad488128a5dbb3488b8d54f7b73b59
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# MDVA-22383: indexadores de regras de destino lentos para indexar

O patch MDVA-22383 resolve o problema em que a reindexação dos indexadores Produto/Regra de destino e Regra de destino/Produto está demorando muito. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20 está instalada. A ID do patch é MDVA-22383. Observe que o problema foi corrigido no Adobe Commerce 2.3.5.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:** Adobe Commerce na infraestrutura em nuvem 2.3.2

**Compatível com as versões do Adobe Commerce:** Adobe Commerce na infraestrutura de nuvem e Adobe Commerce no local 2.3.0-2.3.3-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A reindexação dos indexadores de Produto/Regra de destino e Regra de destino/Produto está demorando muito.

<u>Pré-requisitos:</u> o problema ocorre quando há um grande número de produtos.

<u>Etapas a serem reproduzidas:</u>

1. Para criar uma regra de destino com produtos que correspondam às condições, as condições devem adicionar mais produtos à coleção e devem ter atributos (não categorias ou conjunto de atributos).
1. Execute o seguinte comando:

   ```bash
       bin/magento indexer:reindex targetrule_product_rule
   ```

<u>Resultado real:</u>

A reindexação está paralisada; a economia de produtos está paralisada.

<u>Resultado esperado:</u>

A reindexação foi concluída com sucesso.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte a seção [Patches disponíveis no QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
