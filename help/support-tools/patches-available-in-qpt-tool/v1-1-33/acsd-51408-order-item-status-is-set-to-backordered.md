---
title: "ACSD-51408: o status do item do pedido está definido incorretamente como [!UICONTROL backordered]"
description: Aplique o patch ACSD-51408 para corrigir o problema do Adobe Commerce em que o status do item do pedido está incorretamente definido como [!UICONTROL backordered].
feature: B2B, Orders
role: Admin
exl-id: 0355beca-4612-438f-8f91-be42d8d637e9
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# ACSD-51408: O status do item de pedido está definido incorretamente como *[!UICONTROL backordered]*

O patch ACSD-51408 corrige o problema em que o status do item do pedido é definido incorretamente como [!UICONTROL backordered]. Este patch está disponível quando o [!DNL Quality Patches Tool (QPT)] 1.1.33 está instalado. A ID do patch é ACSD-51408. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.7 - 2.4.6-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O status do item do pedido está incorretamente configurado para *[!UICONTROL backordered]*.

<u>Pré-requisitos</u>:

Os módulos B2B e Inventory management (MSI) do Adobe Commerce são instalados.

<u>Etapas a serem reproduzidas</u>:

1. Crie um novo site, loja e exibição de loja.
1. Crie uma nova fonte.
1. Crie um novo estoque vinculado ao novo site criado na etapa 1 e atribua a fonte criada na etapa 2.
1. Crie uma empresa e atribua-a ao novo site criado na etapa 1.
1. Crie um novo cliente e atribua-o à empresa criada na etapa 4.
1. Crie um produto, atribua-o ao novo site e defina o **[!UICONTROL default stock]** = *0* e o **[!UICONTROL new stock]** como maior que *0*.
1. Habilitar **[!UICONTROL backorders]**.
1. Habilitar o método de pagamento **[!UICONTROL Check/Money Order]** para o novo escopo de site.
1. Habilite o **[!UICONTROL Flat Rate shipping method]** para o novo escopo de site.
1. Criar um novo pedido em **[!UICONTROL Admin]** > **[!UICONTROL Sales]** > **[!UICONTROL Orders]** > **[!UICONTROL Create New Order]**.
1. Selecione o novo cliente criado na etapa 5.
1. Selecione o novo armazenamento criado na etapa 1.
1. Escolha o produto criado na etapa 6.
1. Preencha as informações do pedido, incluindo os métodos de pagamento e envio.
1. Enviar o pedido.
1. Verifique o *Status do Item*.

<u>Resultados esperados</u>

O item está disponível para entrega no inventário. O status do item é *[!UICONTROL ordered]*.

<u>Resultados reais</u>

O status do item é *[!UICONTROL backordered]*.

>[!MORELIKETHIS]
>
>[O status do item de pedido está incorretamente definido como *[!UICONTROL Ordered]* quando o estoque de produtos é 0.](/help/support-tools/patches-available-in-qpt-tool/v1-1-33/acsd-51735-order-item-status-incorrectly-set.md)

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] versão: uma nova ferramenta para autoatender patches de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando o [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
