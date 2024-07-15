---
title: "ACSD-44938: VAT_ID não pode ser aplicado na solicitação do GraphQL para o usuário convidado"
description: O patch ACSD-44938 corrige o problema em que a VAT_ID não pode ser aplicada em uma solicitação GraphQL para um usuário convidado. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.18 está instalada. A ID do patch é ACSD-44938. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.
exl-id: 18b3dfa5-b666-491e-a067-526a53294f39
feature: Admin Workspace, GraphQL
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 0%

---

# ACSD-44938: VAT_ID não pode ser aplicado na solicitação GraphQL para o usuário convidado

O patch ACSD-44938 corrige o problema em que a VAT_ID não pode ser aplicada em uma solicitação GraphQL para um usuário convidado. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.18 está instalada. A ID do patch é ACSD-44938. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.0 - 2.4.3-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

VAT_ID não pode ser aplicado em uma solicitação GraphQL para um usuário convidado.

<u>Etapas a serem reproduzidas</u>:

1. Siga as etapas mencionadas no [tutorial do GraphQL](https://devdocs.magento.com/guides/v2.4/graphql/tutorials/checkout/checkout-shopping-cart.html) em nossa documentação do desenvolvedor para criar um carrinho de convidado.
1. Tente aplicar VAT_ID para o usuário convidado usando o GraphQL.

<u>Resultados esperados</u>:

VAT_ID pode ser aplicado da mesma forma que para um cliente registrado. Consulte o artigo [createCustomerAddress mutation](https://devdocs.magento.com/guides/v2.4/graphql/mutations/create-customer-address.html) na documentação do desenvolvedor.

<u>Resultados reais</u>:

VAT_ID não pode ser aplicado a um usuário convidado usando GraphQL.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.
