---
title: "Patch MDVA-32714: o preço do grupo de clientes não está funcionando via GraphQL"
description: O patch MDVA-32714 corrige o problema em que сo preço de grupo de clientes não é adicionado na resposta de consulta de produto do GraphQL. Este patch está disponível quando a Ferramenta de correções de qualidade (QPT) 1.0.13 está instalada. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.3.
exl-id: a4fc92ad-68dc-437d-8577-303007ef8a92
feature: GraphQL, Customer Service, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 0%

---

# Correção do MDVA-32714: o preço do grupo de clientes não está funcionando via GraphQL

>[!WARNING]
>
>Um novo patch chamado MDVA-33975 corrige problemas de cálculo de preço do GraphQL. O MDVA-32714 está depreciado e recomenda-se a aplicação do patch MDVA-33975. Para acessar este patch, consulte o [patch MDVA-33975: cálculos de preço do GraphQL](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/mdva-33975-magento-patch-graphql-price-calculations.html) em nossa base de dados de conhecimento de suporte.

O patch MDVA-32714 corrige o problema em que сo preço de grupo de clientes não é adicionado na resposta de consulta de produto do GraphQL. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.13 está instalada. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.3.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

Adobe Commerce na infraestrutura em nuvem 2.4.0

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce na infraestrutura em nuvem e Adobe Commerce no local 2.3.4 - 2.4.0-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O preço de grupo do cliente para o cliente geral não é adicionado na resposta de consulta de produto da GraphQL.

<u>Etapas a serem reproduzidas</u>:

1. Ative e defina Preço Especial para qualquer produto para qualquer grupo de clientes.
1. Use a consulta de produto no GraphQL para obter preços para este produto, conforme descrito em: [Consulta de produtos > Consulta de exemplo](https://devdocs.magento.com/guides/v2.4/graphql/queries/products.html#sample-queries) em nossa documentação de desenvolvedor.

<u>Resultados esperados</u>:

```api
price_range
```

exibe o preço com desconto para clientes em geral de acordo com o que foi definido no Painel de administração.

<u>Resultados reais</u>:

```api
price_range
```

não exibe o preço com desconto para clientes em geral.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte os [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.
