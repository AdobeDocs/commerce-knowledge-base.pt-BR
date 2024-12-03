---
title: 'ACSD-51735: Status do item de pedido definido incorretamente como *[!UICONTROL Ordered]* quando o estoque de produtos é 0'
description: Aplique o patch ACSD-51735 para corrigir o problema do Adobe Commerce em que o status do item do pedido é definido incorretamente como *[!UICONTROL Ordered]* quando o estoque do produto é 0.
feature: Orders, Products
role: Admin
exl-id: c6376698-71dc-46b8-a5b2-86dc26a574ab
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 0%

---

# ACSD-51735: Status do item de pedido definido incorretamente como *[!UICONTROL Ordered]* quando o estoque do produto é 0

O patch ACSD-51735 corrige o problema em que o status do item do pedido é definido incorretamente como *[!UICONTROL Ordered]* quando o estoque do produto é 0. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.33 está instalado. A ID do patch é ACSD-50895. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.4-p4

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O status do item do pedido está incorretamente definido como *[!UICONTROL Ordered]* quando o estoque do produto é 0.

<u>Pré-requisitos</u>:

* Os módulos Adobe Commerce Inventory management (MSI) são instalados.
* Os pedidos pendentes estão habilitados em **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Product Stock Options]** > **[!UICONTROL Backorders]**.

<u>Etapas a serem reproduzidas</u>:

1. Criar um novo estoque.
1. Crie uma nova fonte.
1. Atribua o site padrão ao novo estoque e atribua a nova fonte.
1. Crie um novo produto.

   * Defina a Quantidade de origem padrão como 10 e a nova Quantidade de origem como 0.

1. Adicione o produto ao carrinho na loja.
1. Observe o aviso de backorder na finalização da compra, indicando que o produto vem de uma nova fonte.
1. Coloque o pedido.
1. Abra o pedido em Admin e verifique o status do backorder.

<u>Resultados esperados</u>:

A ordem mostra que a Qtde. 1 está em backorder.

<u>Resultados reais</u>:

A ordem mostra que a Qtd. 1 é solicitada, não está em backorder.

>[!MORELIKETHIS]
>
>[O status do item da ordem está configurado incorretamente como *[!UICONTROL Backordered]*](/help/support-tools/patches-available-in-qpt-tool/v1-1-33/acsd-51408-order-item-status-is-set-to-backordered.md)

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] versão: uma nova ferramenta para autoatender patches de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando o [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
