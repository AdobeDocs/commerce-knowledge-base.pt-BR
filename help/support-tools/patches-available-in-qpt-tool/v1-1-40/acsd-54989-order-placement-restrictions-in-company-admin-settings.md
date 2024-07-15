---
title: "ACSD-54989: o administrador da empresa não pode fazer pedidos quando [!UICONTROL Enable Purchase Orders] está definido como Sim e [!UICONTROL Purchase Order] está definido como Não"
description: Aplique o patch ACSD-54989 para corrigir o problema do Adobe Commerce em que o administrador da empresa não pode fazer pedidos se [!UICONTROL Enable Purchase Orders] estiver definido como Sim e [!UICONTROL Purchase Order] estiver definido como Não.
feature: Orders, Companies, Purchase Orders
role: Admin, Developer
exl-id: c2850409-d310-4681-80ec-af8ba347854c
source-git-commit: 35cd21581ee34a6213be42a79e159439b8856fb6
workflow-type: tm+mt
source-wordcount: '389'
ht-degree: 0%

---

# ACSD-54989: O administrador da empresa não pode fazer pedidos quando *[!UICONTROL Enable Purchase Orders]* está definido como *Sim* e *[!UICONTROL Purchase Order]* está definido como *Não*

O patch ACSD-54989 corrige o problema em que os pedidos não podem ser feitos se **[!UICONTROL Enable Purchase Orders]** estiver definido como *Sim* e **[!UICONTROL Purchase Order]** definido como *Não*. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.40 está instalado. A ID do patch é ACSD-54989. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4-p5 - 2.4.6-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os administradores da empresa não podem fazer pedidos quando **[!UICONTROL Enable Purchase Orders]** está definido como *Sim* e **Ordem de Compra** está definido como *Não*.

<u>Pré-requisitos</u>:

Instalar [!DNL B2B] módulos.

<u>Etapas a serem reproduzidas</u>:

1. Habilite a empresa e saia [!UICONTROL **Order Approval Configuration]** > **[!UICONTROL Purchase Order**] = *Não*.
1. Crie um produto simples com um preço de 100.
1. Crie uma nova empresa por meio do Administrador.
1. Defina [!UICONTROL **Habilitar Ordens de Compra**] para *Sim*.
1. Faça logon como o administrador da empresa na loja.
1. Adicione o produto simples criado ao carrinho.
1. Vá para a página de check-out e clique em **[!UICONTROL Place Order]** para concluir a compra.

<u>Resultados esperados</u>:

Você pode fazer um pedido com sucesso.

<u>Resultados reais</u>:

A página **[!UICONTROL My Account]** é aberta e o pedido não é feito.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] versão: uma nova ferramenta para autoatender patches de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando o [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
