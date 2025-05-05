---
title: 'MDVA-40134: o GraphQL não retorna produtos relacionados quando o catálogo compartilhado está habilitado'
description: O patch MDVA-40134 corrige o problema em que o GraphQL não retorna produtos relacionados quando o catálogo compartilhado está ativado. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2 está instalada. A ID do patch é MDVA-40134. Observe que o problema foi corrigido no Adobe Commerce 2.4.3.
exl-id: 7b14355a-1c14-4c80-9426-6c40505d638b
feature: B2B, Catalog Management, GraphQL, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 0%

---

# MDVA-40134: o GraphQL não retorna produtos relacionados quando o catálogo compartilhado está habilitado

O patch MDVA-40134 corrige o problema em que o GraphQL não retorna produtos relacionados quando o catálogo compartilhado está ativado. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2 está instalada. A ID do patch é MDVA-40134. Observe que o problema foi corrigido no Adobe Commerce 2.4.3.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.4.2-p1

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.4.2-p1 - 2.4.2-p2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O GraphQL não retorna produtos relacionados quando o catálogo compartilhado está habilitado.

<u>Pré-requisitos</u>:

Os módulos B2B devem ser instalados.
A instância deve ser limpa somente com os dados de amostra.

<u>Etapas a serem reproduzidas</u>:

1. Vá para **Lojas** > **Configuração** > **Geral** > **Recursos B2B** e habilite a **Empresa e Catálogo Compartilhado**.
1. Vá para **Catálogo** > **Catálogo Compartilhado** e adicione todos os produtos ao **Catálogo Geral**.
1. Use os dados de amostra e modifique o Joust Duffle Bag (SKU 24-MB01).
1. Em **Produtos relacionados**, adicione as duas bolsas Duffle (ID 7 e 13).
1. Enviar uma solicitação **Post**:

<pre>&lbrace;
  products(filtro: {sku: {eq: "24-MB01"}}, classificar: {name: ASC}) &lbrace;
    itens &lbrace;
      related_products &lbrace;
        uid
        name
      &rbrace;
    &rbrace;
  &rbrace;
&rbrace;</pre>

<u>Resultados esperados</u>:

Os produtos relacionados são mostrados na resposta da GraphQL.

<u>Resultados reais</u>:

Os usuários recebem o seguinte erro:

<pre>O valor de retorno de Magento\CatalogPermissionsGraphQl\Model\Store\StoreProcessor::getStoreId() deve ser do tipo int, null retornado &lbrace;"exception":"[object] (GraphQL\\Error\\Error(code: 0): O valor de retorno de Magento\\CatalogPermissionsGraphQl\\Model\\Store\\StoreProcessor::getStoreId() deve ser do tipo int, null retornado </pre>

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) na documentação do desenvolvedor.
