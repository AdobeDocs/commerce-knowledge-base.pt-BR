---
title: '"ACSD-54989: o administrador da empresa não pode fazer pedidos quando [!UICONTROL Enable Purchase Orders] defina como Sim e [!UICONTROL Purchase Order] definir como Não'''
description: Aplique o patch ACSD-54989 para corrigir o problema do Adobe Commerce em que o administrador da empresa não pode fazer pedidos se [!UICONTROL Enable Purchase Orders] está definido como Sim e [!UICONTROL Purchase Order] está definida como Não.
feature: Orders, Companies, Purchase Orders
role: Admin, Developer
exl-id: c2850409-d310-4681-80ec-af8ba347854c
source-git-commit: 35cd21581ee34a6213be42a79e159439b8856fb6
workflow-type: tm+mt
source-wordcount: '389'
ht-degree: 0%

---

# ACSD-54989: o administrador da empresa não pode fazer pedidos quando *[!UICONTROL Enable Purchase Orders]* definir como *Sim* e *[!UICONTROL Purchase Order]* definir como *Não*

O patch ACSD-54989 corrige o problema em que os pedidos não podem ser feitos se **[!UICONTROL Enable Purchase Orders]** definir como *Sim* e **[!UICONTROL Purchase Order]** definir como *Não*. Este patch está disponível quando a variável [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.40 está instalado. A ID do patch é ACSD-54989. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4-p5 - 2.4.6-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os administradores de empresas não podem fazer pedidos quando **[!UICONTROL Enable Purchase Orders]** está definida como *Sim* e **Ordem de Compra** definir como *Não*.

<u>Pré-requisitos</u>:

Instalar [!DNL B2B] módulos.

<u>Etapas a serem reproduzidas</u>:

1. Habilitar empresa e sair [!UICONTROL **Order Approval Configuration]** > **[!UICONTROL Purchase Order**] = *Não*.
1. Crie um produto simples com um preço de 100.
1. Crie uma nova empresa por meio do Administrador.
1. Definir [!UICONTROL **Habilitar Ordens de Compra**] para *Sim*.
1. Faça logon como o administrador da empresa na loja.
1. Adicione o produto simples criado ao carrinho.
1. Vá para a página de check-out e clique em **[!UICONTROL Place Order]** para concluir a compra.

<u>Resultados esperados</u>:

Você pode fazer um pedido com sucesso.

<u>Resultados reais</u>:

A variável **[!UICONTROL My Account]** será aberta e o pedido não será feito.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.
