---
title: "Patch MDVA-31640: não é possível criar atualização agendada consecutiva via API REST"
description: O patch MDVA-31640 corrige o problema em que uma nova atualização agendada para o preço especial não pode ser criada para várias lojas usando a API REST, se a data de início da atualização coincidir com a data de término da atualização existente anteriormente. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.9 está instalada. Observe que o problema foi corrigido no Adobe Commerce 2.4.2.
exl-id: 8d91db3d-7c94-4757-8087-4cf53cad81e7
feature: REST
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '539'
ht-degree: 0%

---

# Patch MDVA-31640: não é possível criar atualização agendada consecutiva via API REST

O patch MDVA-31640 corrige o problema em que uma nova atualização agendada para o preço especial não pode ser criada para várias lojas usando a API REST, se a data de início da atualização coincidir com a data de término da atualização existente anteriormente. Este patch está disponível quando a variável [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.0.9 está instalado. Observe que o problema foi corrigido no Adobe Commerce 2.4.2.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

Adobe Commerce na infraestrutura em nuvem 2.3.5-p1

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce na infraestrutura em nuvem e Adobe Commerce no local 2.3.1 - 2.3.5-p2, 2.4.0, 2.4.0-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Corrige o problema em que uma nova atualização agendada para o preço especial não pode ser criada para várias lojas usando a API REST, se a data de início da atualização coincidir com a data de término da atualização existente anteriormente.

<u>Etapas a serem reproduzidas</u>:

1. Configure uma visualização adicional do site, loja e loja.
1. Crie dois produtos simples: &quot;product1&quot; e &quot;product2&quot;.
1. Atribua o produto1 a um site e o produto2 a ambos os sites.
1. Crie uma atualização programada para o preço especial referente a product1 na exibição de loja para a loja com ID 1. Usar API REST `POST` solicitação para `rest/V1/products/special-price` com a seguinte carga:
   `{        "prices": [            {                "price": 15,                "store_id": 1,                "sku": "product1",                "price_from": "2021-11-15 04:00:00",                "price_to": "2021-11-15 04:10:00"            }        ]    }`
1. Crie uma atualização programada para o preço especial do produto2 em ambas as exibições da loja para lojas com ID 1 e 2 usando a API REST `POST` solicitação para `rest/V1/products/special-price` com a seguinte carga (a variável `price_from` a data é igual a `price_to` data do pedido anterior):
   `{        "prices": [            {                "price": 14,                "store_id": 1,                "sku": "product2",                "price_from": "2021-11-15 04:10:00",                "price_to": "2021-11-15 04:15:00"            },            {                "price": 13,                "store_id": 2,                "sku": "product2",                "price_from": "2021-11-15 04:10:00",                "price_to": "2021-11-15 04:15:00"            }        ]    }`

<u>Resultados esperados</u>:

A atualização agendada com a alteração de preço especial é criada em ambas as exibições de loja.

<u>Resultados reais</u>:

O Adobe Commerce lança um erro. A atualização agendada não foi criada.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de atualização de software > Aplicar patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatendimento de correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de patches de qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte o [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.
