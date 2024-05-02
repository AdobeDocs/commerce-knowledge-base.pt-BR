---
title: "MDVA-40134: o GraphQL não retorna produtos relacionados quando o catálogo compartilhado está habilitado"
description: O patch MDVA-40134 corrige o problema em que o GraphQL não retorna produtos relacionados quando o catálogo compartilhado está ativado. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2 está instalada. A ID do patch é MDVA-40134. Observe que o problema foi corrigido no Adobe Commerce 2.4.3.
exl-id: 7b14355a-1c14-4c80-9426-6c40505d638b
feature: B2B, Catalog Management, GraphQL, Products
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 0%

---

# MDVA-40134: o GraphQL não retorna produtos relacionados quando o catálogo compartilhado está habilitado

O patch MDVA-40134 corrige o problema em que o GraphQL não retorna produtos relacionados quando o catálogo compartilhado está ativado. Este patch está disponível quando a variável [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.2 está instalado. A ID do patch é MDVA-40134. Observe que o problema foi corrigido no Adobe Commerce 2.4.3.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.4.2-p1

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.4.2-p1 - 2.4.2-p2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O GraphQL não retorna produtos relacionados quando o catálogo compartilhado está habilitado.

<u>Pré-requisitos</u>:

Os módulos B2B devem ser instalados.
A instância deve ser limpa somente com os dados de amostra.

<u>Etapas a serem reproduzidas</u>:

1. Ir para **Lojas** > **Configuração** > **Geral** > **Recursos B2B** e habilitar **Catálogo de Empresas e Compartilhado**.
1. Ir para **Catálogo** > **Catálogo compartilhado** e adicione todos os produtos à **Catálogo geral**.
1. Use os dados de amostra e modifique o Joust Duffle Bag (SKU 24-MB01).
1. Em **Produtos relacionados**, adicione as duas bolsas Duffle (ID 7 e 13).
1. Enviar um **Publicar** solicitação:

<pre>{ products(filtro: {sku: {eq: "24-MB01"}}, sort: {name: ASC}) { items { related_products { uid name } } } }</pre>

<u>Resultados esperados</u>:

Os produtos relacionados são mostrados na resposta da GraphQL.

<u>Resultados reais</u>:

Os usuários recebem o seguinte erro:

<pre>O valor de retorno de Magento\CatalogPermissionsGraphQl\Model\Store\StoreProcessor::getStoreId() deve ser do tipo int, null retornado {"exception":"[object] (GraphQL\\Error\\Error(code: 0): O valor de retorno de Magento\\CatalogPermissionsGraphQl\\Model\\Store\\StoreProcessor::getStoreId() deve ser do tipo int, null retornado </pre>

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de atualização de software > Aplicar patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatendimento de correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de patches de qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.
