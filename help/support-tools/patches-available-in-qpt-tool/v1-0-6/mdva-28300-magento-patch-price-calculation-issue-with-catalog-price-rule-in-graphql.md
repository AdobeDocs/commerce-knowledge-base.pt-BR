---
title: "MDVA-28300: problema de cálculo de preço com regra de preço de catálogo no GraphQL"
description: O patch MDVA-28300 corrige o problema em que a solicitação do GraphQL não reflete as alterações de preço das regras de preço do catálogo. Este patch está disponível quando a Ferramenta de correções de qualidade (QPT) v.1.0.6 é instalada. Observe que o problema foi corrigido no Adobe Commerce versão 2.3.6.
exl-id: 86079d29-db69-4758-a159-aeed8e0ea21f
feature: Catalog Management, GraphQL, Customer Service, Marketing Tools, Orders, Price Rules
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '513'
ht-degree: 0%

---

# MDVA-28300: problema de cálculo de preço com regra de preço de catálogo no GraphQL

>[!WARNING]
>
>Um novo patch chamado MDVA-33975 corrige problemas de cálculo de preço do GraphQL. O MDVA-28300 está depreciado e recomenda-se a aplicação do patch MDVA-33975. Para acessar este patch, consulte [MDVA-33975: cálculos de preço do GraphQL](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/mdva-33975-magento-patch-graphql-price-calculations.html).

O patch MDVA-28300 corrige o problema em que a solicitação do GraphQL não reflete as alterações de preço das regras de preço do catálogo. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.6 está instalada. Observe que o problema foi corrigido no Adobe Commerce versão 2.3.6.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:** Adobe Commerce no local 2.3.5-p1

**Compatível com as versões do Adobe Commerce:** Adobe Commerce no local e Adobe Commerce na infraestrutura em nuvem 2.3.0 - 2.3.5-p2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Quando uma regra de preço de catálogo é aplicada a um determinado grupo de clientes, os preços de itens no carrinho e o total do pedido não são calculados corretamente no GraphQL.

<u>Etapas a serem reproduzidas:</u>

1. Crie uma nova conta de cliente e altere seu Grupo de Clientes para Atacado.
1. Crie uma nova regra de Catálogo em **Marketing** > **Promoções** > **Regras de Preço de Catálogo** com os seguintes parâmetros:
   * Grupos de Clientes: Ações de Atacado:
   * Aplicar: *Aplicar como porcentagem do original*
   * Desconto: *50*


1. Crie um novo produto com preço=100.
1. Faça logon no front-end usando a conta de cliente criada anteriormente (se você já tiver feito logon, faça logoff e logon novamente).
1. Adicione o produto ao carrinho. O preço do produto é 50 (preço normal 100) e Pedido total: 55 (50 + 5 do custo de envio).
1. Execute a chamada à API do GraphQL descrita na [consulta ao carrinho do cliente](https://devdocs.magento.com/guides/v2.3/graphql/queries/customer-cart.html) em nossa documentação para desenvolvedores.

<u>Resultado esperado:</u>

A API e o front-end têm o mesmo total de pedido com o desconto introduzido pela regra de catálogo que está sendo aplicada.

<u>Resultado real:</u>

O total do pedido não aplica o desconto de regra de catálogo.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Aplique patches usando a Ferramenta de Patches de Qualidade](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e Patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html).

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte Patches disponíveis na seção QPT.
