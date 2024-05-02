---
title: 'MDVA-43601: os acionadores são removidos da tabela "catalog_product_price" após o reindexação completo'
description: O patch MDVA-43601 corrige o problema em que os acionadores são removidos da tabela "catalog_product_price" após um reindexação completo de "catalog_rule" ou "catalog_product". Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13 está instalada. A ID do patch é MDVA-43601. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.
exl-id: fdef1e56-79ec-455a-8a29-b82f1c8ceea7
feature: Catalog Management, Orders, Products
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# MDVA-43601: os acionadores são removidos da tabela &quot;catalog_product_price&quot; após o reindexação completo

O patch MDVA-43601 corrige o problema em que os acionadores são removidos do `catalogrule_product_price` tabela após um reindexação completa de `catalogrule_rule` ou `catalogrule_product`. Este patch está disponível quando a variável [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.13 está instalado. A ID do patch é MDVA-43601. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.0 - 2.4.4

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os acionadores são removidos do `catalogrule_product_price` tabela após um reindexação completa de `catalogrule_rule` ou `catalogrule_product`.

<u>Etapas a serem reproduzidas</u>:

1. Definir todos os indexadores como *Atualização por Agendamento*.
1. Verifique os acionadores criados para `catalogrule_product_price` executando a seguinte solicitação SQL:

   ```sql
   show triggers like '%catalogrule_%'\G
   ```

1. Reindexar manualmente `catalogrule_rule` ou `catalogrule_product` executando o seguinte comando: `bin/magento indexer:reindex catalogrule_rule`
1. Verifique os acionadores de `catalogrule_product_price` tabela novamente.

<u>Resultados esperados</u>:

Acionadores em `catalogrule_product_price` As tabelas são preservadas após um reindexação completo.

<u>Resultados reais</u>:

Nenhum acionador encontrado para `catalogrule_product_price` tabela.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de atualização de software > Aplicar patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatendimento de correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de patches de qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.
