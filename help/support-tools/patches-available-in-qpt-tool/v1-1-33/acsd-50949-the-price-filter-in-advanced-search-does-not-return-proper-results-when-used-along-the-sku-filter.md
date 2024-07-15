---
title: "ACSD-50949: o filtro de preço na pesquisa avançada não retorna resultados adequados quando usado junto com o filtro SKU"
description: Aplique o patch ACSD-50949 para corrigir o problema do Adobe Commerce em que o filtro de preço na pesquisa avançada não retorna resultados adequados quando usado junto com o filtro SKU.
feature: Orders, Search
role: Admin
exl-id: 3e1f88dc-07f6-4e10-b4b7-163648076cbc
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 1%

---

# ACSD-50949: o filtro de preço na pesquisa avançada não retorna os resultados adequados quando usado com o filtro SKU

O patch ACSD-50949 corrige o problema em que o filtro de preço na pesquisa avançada não retorna resultados adequados quando usado junto com o filtro SKU. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.33 está instalado. A ID do patch é ACSD-50949. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2 - 2.4.6-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>). Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Problema

O filtro de preço na pesquisa avançada não retorna resultados adequados quando usado junto com o filtro SKU.

<u>Etapas a serem reproduzidas</u>:

1. Crie vários produtos, por exemplo:

   | SKU | Nome | Preço | Quantidade |
   |-----|-----------|-------|----------|
   | MJ1 | Product 1 | $ 10 | 10 |
   | MJ2 | Product 2 | $ 15 | 10 |
   | MJ3 | Product 3 | $ 21 | 10 |
   | MJ4 | Product 4 | $ 32 | 10 |
   | MJ5 | Product 5 | $ 33 | 10 |
   | MJ6 | Product 6 | $ 34 | 10 |
   | MJ7 | Product 7 | $ 44 | 10 |

1. Abra o **[!UICONTROL Advanced Search]** na Loja e pesquise por SKU: &quot;MJ&quot;.
1. Clique no link **[!UICONTROL Modify your search]**.
1. Adicione um intervalo de preços aos critérios de *1* a *21* e clique no botão **[!UICONTROL Search]**.

<u>Resultados esperados</u>:

Somente os produtos com preços na faixa definida são retornados.

<u>Resultados reais</u>:

Produtos com preços superiores a *$21* são devolvidos.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] versão: uma nova ferramenta para autoatender patches de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando o [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) no guia [!DNL Quality Patches Tool].
