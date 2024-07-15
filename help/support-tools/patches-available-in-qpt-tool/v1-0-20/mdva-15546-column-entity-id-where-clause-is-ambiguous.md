---
title: "MDVA-15546: Coluna 'entity_id' onde a cláusula é ambígua"
description: "O patch MDVA-15546 resolve problemas de desempenho que podem estar relacionados a algumas extensões do Amazon. Esse problema é indicado pelo seguinte erro nos logs de exceção: *onde*   *Coluna 'entity\\_id' em onde a cláusula é ambígua, a consulta foi: SELECT \\`main\\_table\\`.\\*, \\`extension\\_attribute\\_amazon\\_order\\_reference\\_id* \\`. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20 está instalada. A ID do patch é MDVA-15546."
exl-id: d58c1728-eb7a-49e8-a329-3197f2339b9c
feature: B2B, Commerce Intelligence
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 0%

---

# MDVA-15546: Coluna &#39;entity_id&#39; onde a cláusula é ambígua

O patch MDVA-15546 resolve problemas de desempenho que podem estar relacionados a algumas extensões do Amazon. Esse problema é indicado pelo seguinte erro nos logs de exceção: *onde*   *Coluna &#39;entity\_id&#39; em onde a cláusula é ambígua, a consulta foi: SELECT \`main\_table\`.\*, \`extension\_attribute\_amazon\_order\_reference\_id* \`. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20 está instalada. A ID do patch é MDVA-15546.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

Adobe Commerce na infraestrutura em nuvem 2.2.5

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce na infraestrutura em nuvem 2.3.0 - 2.4.2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Problemas de desempenho que podem estar relacionados a algumas extensões do Amazon.

<u>Pré-requisitos</u>:

Limpar o Adobe Commerce com B2B e Amazon\_Payment.

<u>Etapas a serem reproduzidas</u>:

1. Vá para a página da loja.
1. Adicionar produto ao carrinho.
1. Aguarde ou acione o trabalho cron `flush_preview_quotas`.

<u>Resultado real</u>:

Ao marcar `var/log/exception/log`, você verá o seguinte erro:

*`report.ERROR: Cron Jobflush_preview_quotashas an error: SQLSTATE[23000]: Integrity constraint violation: 1052 Column 'entity_id' in where clause is ambiguous, query was: SELECT `tabela_principal`.*, `atributo_de_extensão_amazon_order_reference_id`.`amazon_order_reference_id` AS `atributo_de_extensão_amazon_order_id_de_referência_amazon_order_id`, `atributo_de_extensão_amazon_order_reference_id`.`id_de_referência_de_atributo_de_extensão_amazon_id_de_referência_de_ordem_de_extensão_id`, `atributo_de_extensão_amazon_id_de_referência_de_ordem_de_extensão`.` sandbox_reference_reference_box simulation_reference`, `extension_attribute_amazon_order_reference_id`.`confirm` AS `extension_attribute_amazon_order_reference_id_confirm` FROM `quote` AS `main_table` LEFT JOIN `amazon_quote` AS `extension_attribute_amazon_order_reference_id` ON main_table.entity_id = extension_attribute_amazon_order_reference_id.quote_id WHERE ...`*` AS `` AS `

<u>Resultado esperado</u>:

O Cron Job é concluído sem erros.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.
