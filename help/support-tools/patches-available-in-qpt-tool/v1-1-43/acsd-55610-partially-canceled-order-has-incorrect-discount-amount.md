---
title: "ACSD-55610: a ordem parcialmente cancelada tem valor de desconto incorreto"
description: Aplique o patch ACSD-55610 para corrigir o problema do Adobe Commerce em que um pedido parcialmente cancelado tem uma quantia de desconto incorreta.
feature: Invoices, Orders, Price Rules, Shopping Cart
role: Admin, Developer
exl-id: f4cca4fa-dc04-4c86-9176-c648b1d0e732
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# ACSD-55610: a ordem parcialmente cancelada tem quantia de desconto incorreta

O patch ACSD-55610 corrige o problema em que um pedido parcialmente cancelado tem um valor de desconto incorreto. Este patch está disponível quando o [!DNL Quality Patches Tool (QPT)] 1.1.43 está instalado. A ID do patch é ACSD-55610. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Um pedido parcialmente cancelado tem um valor de desconto incorreto.

<u>Etapas a serem reproduzidas</u>:

1. Criar uma regra de preço de carrinho de compras.

   * *[!UICONTROL Rule Name]*: *Vendas de inverno*
   * *[!UICONTROL Active]* = *Sim*
   * *[!UICONTROL Websites]* = *Site Principal*
   * Escolha todos os grupos de clientes.
   * Selecione um cupom específico.
   * *[!UICONTROL Coupon Code]*: *INVERNO10*
   * *[!UICONTROL Conditions]*: *[!UICONTROL If ALL of these conditions are TRUE]*: *Subtotal(Excl. Imposto) é igual ou maior que 75*
   * Aplicar *[!UICONTROL Percent of product price discount]*.
   * *[!UICONTROL Discount Amount]*: *10*
   * *[!UICONTROL Discard subsequent rules]*: *Sim*

1. Crie três produtos com preços definidos como 100.
1. Adicione os três produtos ao carrinho.
1. Aplique o cupom.
1. Coloque o pedido.
1. Faturar um item da ordem e entregá-lo.
1. Cancele os outros dois itens.
1. Verifique a coluna `base_discount_canceled`.

<u>Resultados esperados</u>:

O valor do desconto em `base_discount_cancelled` reflete corretamente.

<u>Resultados reais</u>:

O `base_discount_cancelled` não está correto.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] versão: uma nova ferramenta para autoatender patches de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando o [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
