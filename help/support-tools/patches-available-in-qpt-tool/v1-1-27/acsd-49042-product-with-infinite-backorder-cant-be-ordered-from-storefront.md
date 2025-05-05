---
title: 'ACSD-49042: O produto com backorder infinito não pode ser encomendado na loja'
description: Aplique o patch ACSD-49042 para corrigir o problema do Adobe Commerce em que um produto com backorder infinito não pode ser solicitado na loja.
exl-id: b9227296-f300-447c-a241-30ccc0691c9a
feature: Admin Workspace, Orders, Products, Storefront
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# ACSD-49042: O produto com backorder infinito não pode ser encomendado na loja

O patch ACSD-49042 corrige o problema em que um produto com backorder infinito não pode ser solicitado na loja. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.27 está instalado. A ID do patch é ACSD-49042. Observe que o problema foi corrigido no Adobe Commerce 2.4.5.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.4-p2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O erro ocorre quando um produto com backorder infinito não pode ser encomendado na loja.

<u>Etapas a serem reproduzidas</u>:

1. Defina as seguintes definições de configuração:
   * **[!UICONTROL Display Out of Stock Products]** definido como *[!UICONTROL Yes]*.
   * **[!UICONTROL Backorders]** definido como *[!UICONTROL Allow Qty Below 0]*.
1. Adicione um novo **[!DNL custom stock]** e **[!DNL custom source]**.
1. Atribua um produto a **[!DNL custom source]** e verifique se há um número de estoque definido para ele (Por exemplo: *10*).
1. Na página de edição do produto, abra **[!UICONTROL Advanced Inventory]**. Defina o **[!UICONTROL minimum quantity]** no carrinho, (Por exemplo: *160*). A quantidade deve estar acima do estoque.
1. Acesse a loja e compre um produto para criar uma reserva.
1. Altere o **[!UICONTROL product quantity]** para *0*. O ponto crítico é salvar o produto de **[!DNL Admin panel]** quando houver uma reserva.
1. Abra o **[!UICONTROL product page]** na loja e tente adicionar o produto ao carrinho.

<u>Resultados esperados</u>:

É possível adicionar o produto ao carrinho porque pedidos pendentes para uma quantidade abaixo de *0* são permitidos.

<u>Resultados reais</u>:

O produto é exibido como indisponível.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] versão: uma nova ferramenta para autoatender patches de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando o [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
