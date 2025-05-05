---
title: 'MDVA-40120: a classificação DESC/ASC do produto GraphQL não funciona'
description: O patch MDVA-40120 resolve o problema em que a classificação do GraphQL por DESC/ASC não funciona com produtos que têm a mesma relevância ou preço. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.6 está instalada. A ID do patch é MDVA-40120. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.
exl-id: f04373d6-d3e8-47ba-9261-87fad8dff327
feature: GraphQL, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---

# MDVA-40120: a classificação DESC/ASC do produto GraphQL não funciona

O patch MDVA-40120 resolve o problema em que a classificação do GraphQL por DESC/ASC não funciona com produtos que têm a mesma relevância ou preço. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.6 está instalada. A ID do patch é MDVA-40120. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

<u>Pré-requisitos</u>:

Crie alguns produtos diferentes com o mesmo preço.

<u>Etapas a serem reproduzidas</u>:

1. Execute a seguinte consulta do GraphQL:
   <pre>
    <code class="language-graphql">
    &lbrace;
      products(filter: {category_id: {eq: "{{cat_id}}"}}, sort: {relevance: ASC}) &lbrace;
        total_count
        items &lbrace;
          name
          sku
        &rbrace;
      &rbrace;
    &rbrace;
    </code>
    </pre>
1. Verifique a resposta.
1. Altere a ordem de classificação de **ASC** para **DESC** na consulta do GraphQL:
   <pre>
    <code class="language-graphql">
    &lbrace;
      products(filter: {category_id: {eq: "{{cat_id}}"}}, sort: {relevance: DESC}) &lbrace;
        total_count
        items &lbrace;
          name
          sku
        &rbrace;
      &rbrace;
    &rbrace;
    </code>
    </pre>
1. Verifique a resposta.

<u>Resultados esperados</u>:

A lista de produtos na resposta do GraphQL deve ser alterada de acordo com a ordem de classificação.

<u>Resultados reais</u>:

A ordem de classificação permanece inalterada.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) na documentação do desenvolvedor.
