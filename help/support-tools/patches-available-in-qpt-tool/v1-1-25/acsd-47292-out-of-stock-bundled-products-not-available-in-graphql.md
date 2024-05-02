---
title: "ACSD-47292: os produtos empacotados esgotados não estão disponíveis na resposta da GraphQL"
description: Aplique o patch ACSD-47292 para corrigir o problema do Adobe Commerce em que os produtos empacotados indisponíveis não estão disponíveis na resposta do GraphQL, mesmo se "mostrar produtos indisponíveis" estiver definido como Sim.
exl-id: 377dc62f-d1cd-4292-b25d-53c498b772a9
feature: Admin Workspace, Categories, GraphQL, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '443'
ht-degree: 0%

---

# ACSD-47292: os produtos empacotados esgotados não estão disponíveis na resposta da GraphQL

O patch ACSD-47292 corrige o problema em que os produtos empacotados esgotados não estão disponíveis na resposta da GraphQL, mesmo se o [!UICONTROL Display Out-of-Stock Products] está definida como *[!UICONTROL Yes]*. Este patch está disponível quando a variável [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.25 está instalado. A ID do patch é ACSD-47292. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.5-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os produtos empacotados esgotados não estão disponíveis na resposta da GraphQL, mesmo se o [!UICONTROL Display Out-of-Stock Products] está definida como *[!UICONTROL Yes]*.

<u>Etapas a serem reproduzidas</u>:

1. Acesse o Administrador do Adobe Commerce > **[!UICONTROL System]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** e defina o [!UICONTROL Display Out-of-Stock Products] para *[!UICONTROL Yes]*.
1. Crie dois produtos simples, s1 e s2.
1. Tornar s1 indisponível e invisível individualmente e s2 em estoque e invisível individualmente e atribuí-los a uma categoria.
1. Crie um produto agrupado com pelo menos um produto de opção e atribua s1 e s2 a essa opção (tipo de entrada &quot;RadioButton&quot;).
1. Salve o produto agrupado e atribua-o a uma categoria.
1. Vá para a loja e abra este produto incluído. Você verá que a opção s1 indisponível está acinzentada, mas visível.
1. Enviar uma solicitação GraphQL:

```GraphQL
{
  categoryList(filters: { ids: { in: ["3"] } }) {
    id
    name
    products(pageSize: 8, sort: { position: ASC }) {
      total_count
      items {
        id
        sku
        name
        ... on BundleProduct {
          url_key
          items {
            title
            sku
            options {
              quantity
              position
              is_default
              product {
                id
                name
                sku
              }
            }
          }
        }
      }
    }
  }
}
```

<u>Resultados esperados</u>:

a opção de pacote s1 está listada na resposta do GraphQL desde [!UICONTROL Display Out-of-Stock Products] está definida como *[!UICONTROL Yes]* e está visível na loja.

<u>Resultados reais</u>:

a opção de pacote s1 não está listada na resposta do GraphQL.

```GraphQL
"items": [
                                {
                                    "title": "oo1",
                                    "sku": "bundle2",
                                    "options": [
                                        {
                                            "quantity": 1,
                                            "position": 2,
                                            "is_default": false,
                                            "product": {
                                                "id": 2,
                                                "name": "s2",
                                                "sku": "s2"
                                            }
                                        }
                                    ]
                                }
                            ]
```

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.
