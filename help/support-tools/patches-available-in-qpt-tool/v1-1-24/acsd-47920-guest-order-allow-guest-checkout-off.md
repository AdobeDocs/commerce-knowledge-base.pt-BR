---
title: '"ACSD-47920: um usuário convidado pode fazer pedidos por meio da API REST mesmo quando [!UICONTROL Allow Guest Checkout] está desativado'''
description: Aplique o patch ACSD-47920 para corrigir o problema do Adobe Commerce em que os pedidos podem ser feitos por meio da API REST como um usuário convidado mesmo quando a variável [!UICONTROL Allow Guest Checkout] está desativado.
exl-id: 8726eac4-ab19-4232-8e15-270d09bdc0a5
feature: REST, Checkout, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---

# ACSD-47920: um usuário convidado pode fazer pedidos por meio da API REST mesmo quando **[!UICONTROL Allow Guest Checkout]** está desativado

O patch ACSD-47920 corrige o problema em que os pedidos podem ser feitos por meio da API REST como um usuário convidado mesmo quando o **[!UICONTROL Allow Guest Checkout]** está desativado. Este patch está disponível quando a variável [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.24 está instalado. A ID do patch é ACSD-47920. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os pedidos podem ser feitos por meio da API Rest como um usuário convidado, mesmo quando a variável **[!UICONTROL Allow Guest Checkout]** está desativado.

<u>Etapas a serem reproduzidas</u>:

1. Acesse o Administrador do Adobe Commerce > **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Sales]** > **[!UICONTROL Checkout]** > **[!UICONTROL Checkout Options]** > e defina o **[!UICONTROL Allow Guest Checkout]** para _Não_.
1. Use a REST API para adicionar um produto ao carrinho e fazer um pedido.

<u>Resultados esperados</u>:

A API de check-out de convidado retorna um erro *[!UICONTROL Sorry, guest checkout is not available]* se **[!UICONTROL Allow Guest Checkout]** está definida como _Não_.

<u>Resultados reais</u>:

A API de check-out de convidado permite que um pedido seja feito mesmo se **[!UICONTROL Allow Guest Checkout]** está definida como _Não_.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.
