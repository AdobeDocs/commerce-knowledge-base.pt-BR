---
title: "MDVA-44562: ID de armazenamento para itens de cotação substituídos pela ID de armazenamento padrão"
description: O patch MDVA-44562 corrige o problema em que a ID de armazenamento padrão substitui a ID de armazenamento por itens de cotação para solicitações de GraphQL. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.16 está instalada. A ID do patch é MDVA-44562. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.
exl-id: 902bfc05-411d-4a6c-a6e8-cd7376629b0c
feature: Quotes
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%

---

# MDVA-44562: ID de armazenamento para itens de cotação substituídos pela ID de armazenamento padrão

O patch MDVA-44562 corrige o problema em que a ID de armazenamento padrão substitui a ID de armazenamento por itens de cotação para solicitações de GraphQL. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.16 está instalada. A ID do patch é MDVA-44562. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3 - 2.4.4

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A ID da loja para itens de cotação é substituída pela ID da loja padrão para solicitações de GraphQL.

<u>Etapas a serem reproduzidas</u>:

1. Criar uma nova exibição de loja.
1. Crie um novo produto simples com nomes diferentes por exibição de loja.
1. Crie um novo cliente.
1. Obtenha o token de autorização do cliente.

   ```GraphQL
    POST /rest/all/V1/integration/customer/token
    {
      "username": "test@example.com",
      "password": "password"
     }
   ```

1. Crie uma nova cotação para o cliente usando o token de autorização.

   ```GraphQL
   POST rest/default/V1/carts/mine
   ```

1. Adicione um produto ao carrinho.

   ```GraphQL
   POST /rest/default/V1/carts/mine/items
   {
     "cartItem": {
       "sku": "simple1",
       "qty": 1,
       "quote_id": "1"
     }
   }
   ```

1. Obtenha o conteúdo do carrinho para a visualização de loja padrão.

   ```GraphQL
   GET rest/default/V1/carts/mine/
   ```

1. Obtenha o conteúdo do carrinho para a nova visualização de loja.

   ```GraphQL
   GET rest/<store_view_2>/V1/carts/mine/
   ```

<u>Resultados esperados</u>:

A resposta da exibição de nova loja mostra o nome do produto da exibição de nova loja.

<u>Resultados reais</u>:

A resposta da nova exibição da loja mostra a configuração do nome do produto na exibição da loja padrão.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.
