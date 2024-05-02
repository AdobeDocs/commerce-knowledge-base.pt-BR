---
title: '"ACSD-54660: nova classificação de atributo de entrada para classificar pedidos de clientes em [!DNL GraphQL]'''
description: Aplique o patch ACSD-54660 para corrigir o problema do Adobe Commerce em que um novo atributo de entrada "sort" foi adicionado para classificar pedidos do cliente em [!DNL GraphQL] por "sort_field" e "sort_direction".
feature: GraphQL, Orders
role: Admin, Developer
exl-id: 29869139-e5e2-4b00-a090-e2c6673ff9ca
source-git-commit: f12e25ac5dd607cc614dd99c90c5e104b2cee6a8
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 0%

---

# ACSD-54660: Nova classificação de atributo de entrada adicionada para classificar pedidos de clientes em [!DNL GraphQL]

O patch ACSD-54660 corrige o problema em que um novo atributo de entrada `sort` adicionado para classificar ordens do cliente em [!DNL GraphQL] por `sort_field` e `sort_direction`. Este patch está disponível quando a variável [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.39 está instalado. A ID do patch é ACSD-54660. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.5-p5

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Novo atributo de entrada `sort` adicionado para classificar ordens do cliente em [!DNL GraphQL] por `sort_field` e `sort_direction`.

<u>Etapas a serem reproduzidas</u>:

Consultar ordens do cliente usando [!DNL GraphQL]:

```
  {
    customerOrders {
      items {
        order_number
        id
        created_at
        grand_total
        status
      }
    }
  }
```

<u>Resultados esperados</u>:

Este patch adiciona `sort` e `sort_direction` argumentos para `customer.orders`.

<u>Resultados reais</u>:

Não é possível classificar os pedidos usando [!DNL GraphQL].

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.
