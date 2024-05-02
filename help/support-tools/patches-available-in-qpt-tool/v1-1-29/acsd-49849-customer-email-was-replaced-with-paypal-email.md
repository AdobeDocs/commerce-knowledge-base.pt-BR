---
title: "ACSD-49849: o email do cliente foi substituído pelo email do PayPal"
description: Aplique o patch ACSD-49849 para corrigir o problema do Adobe Commerce em que o email do cliente foi substituído pelo email do PayPal ao fazer um pedido no PayPal Express via GraphQL.
exl-id: 826ea90a-ac10-43e8-aa88-bd69b152ded8
feature: Admin Workspace, Communications, Orders, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# ACSD-49849: o email do cliente é substituído por [!DNL PayPal] email

O patch ACSD-49849 corrige o problema em que o email de um cliente é substituído por um [!DNL PayPal's] ao fazer um pedido com o [!DNL PayPal Express] via GraphQL. Este patch está disponível quando a variável [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.29 está instalado. A ID do patch é ACSD-49849. Observe que o problema foi corrigido no Adobe Commerce 2.4.6.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.7 - 2.4.5-p2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O email de um cliente é substituído por um [!DNL PayPal's] ao fazer um pedido com o [!DNL PayPal Express] via GraphQL.

<u>Etapas a serem reproduzidas</u>:

1. Ir para **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Payments]**.
1. Habilitar e configurar [!DNL PayPal Express] e defina **[!UICONTROL Payment Action]** = **[!UICONTROL Sale]**.
1. Ir para **[!UICONTROL Catalog]** > **[!UICONTROL Products]** e criar um produto simples.
1. Conclua o check-out do convidado usando o GraphQL. Para obter mais informações, consulte [Tutorial de check-out do GraphQL](https://developer.adobe.com/commerce/webapi/graphql/tutorials/checkout/) na Documentação do desenvolvedor do Adobe Commerce.
1. Uso [!DNL PayPal Express] como o método de pagamento.
1. Anote o email usado na etapa em que você [configurar seu email para o carrinho](https://developer.adobe.com/commerce/webapi/graphql/tutorials/checkout/set-email-address/) na Documentação do desenvolvedor do Adobe Commerce.
1. Depois que o pedido for feito, vá para o administrador do Adobe Commerce e verifique o email na ordem criada.

<u>Resultados esperados</u>:

O email é o mesmo definido durante o check-out.

<u>Resultados reais</u>:

O email definido durante o check-out é substituído pelo email definido na variável [!DNL PayPal] conta.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.
