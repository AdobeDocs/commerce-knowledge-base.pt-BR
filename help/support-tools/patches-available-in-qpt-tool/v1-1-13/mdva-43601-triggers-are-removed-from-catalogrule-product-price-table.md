---
title: 'MDVA-43601: os acionadores são removidos da tabela "catalog_product_price" após o reindexação completo'
description: O patch MDVA-43601 corrige o problema em que os acionadores são removidos da tabela "catalog_product_price" após um reindexação completo de "catalog_rule" ou "catalog_product". Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13 está instalada. A ID do patch é MDVA-43601. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.
exl-id: fdef1e56-79ec-455a-8a29-b82f1c8ceea7
feature: Catalog Management, Orders, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# MDVA-43601: os acionadores são removidos da tabela &quot;catalog_product_price&quot; após o reindexação completo

O patch MDVA-43601 corrige o problema em que os acionadores são removidos da tabela `catalogrule_product_price` após uma reindexação completa de `catalogrule_rule` ou `catalogrule_product`. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13 está instalada. A ID do patch é MDVA-43601. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.0 - 2.4.4

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os acionadores são removidos da tabela `catalogrule_product_price` após uma reindexação completa de `catalogrule_rule` ou `catalogrule_product`.

<u>Etapas a serem reproduzidas</u>:

1. Defina todos os indexadores como *Atualizar pela Agenda*.
1. Verifique os disparadores criados para a tabela `catalogrule_product_price` executando a seguinte solicitação SQL:

   ```sql
   show triggers like '%catalogrule_%'\G
   ```

1. Reindexar manualmente `catalogrule_rule` ou `catalogrule_product` executando o seguinte comando: `bin/magento indexer:reindex catalogrule_rule`
1. Verifique novamente os acionadores da tabela `catalogrule_product_price`.

<u>Resultados esperados</u>:

Os acionadores na tabela `catalogrule_product_price` são preservados após uma reindexação completa.

<u>Resultados reais</u>:

Nenhum acionador encontrado para a tabela `catalogrule_product_price`.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/usage) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/pt-br/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) na documentação do desenvolvedor.
