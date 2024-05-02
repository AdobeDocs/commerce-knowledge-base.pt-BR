---
title: '"ACSD 49843: link de download do produto indisponível após ser faturado automaticamente com [!UICONTROL Payment Action] = [!UICONTROL Intent Sale]'''
description: Aplique o patch ACSD-49843 para corrigir o problema do Adobe Commerce em que o link de download do produto não está disponível depois que o item solicitado é faturado automaticamente por um método de pagamento online quando [!UICONTROL Payment Action] está definida como [!UICONTROL Intent Sale].
feature: Catalog Management, Configuration, Invoices, Orders, Storefront
role: Admin, Developer
exl-id: 4bfa3827-a2b1-4168-a39c-99c617ee4795
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '487'
ht-degree: 0%

---

# ACSD-49843: link de download do produto indisponível após ser faturado automaticamente com [!UICONTROL Payment Action] = [!UICONTROL Intent Sale]

O patch ACSD-49843 corrige o problema em que o link de download do produto não está disponível depois que o item solicitado é faturado automaticamente por um método de pagamento online quando [!UICONTROL Payment Action] está definida como [!UICONTROL Intent Sale]. Este patch está disponível quando a variável [!DNL Quality Patches Tool (QPT)] O 1.1.37 está instalado. A ID do patch é ACSD-49843. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.7 - 2.3.7-p4, 2.4.1 - 2.4.6-p2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O link de download do produto não estará disponível depois que o item solicitado for faturado automaticamente por um método de pagamento online quando [!UICONTROL Payment Action] está definida como [!UICONTROL Intent Sale].

<u>Etapas a serem reproduzidas</u>:

1. Faça logon no Administrador do Adobe Commerce e navegue até **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Configure Braintree]**.

   * No [!UICONTROL Payment Action] selecione **[!UICONTROL Intent Sale]** e defina *[!UICONTROL Enable Card Payments]* para *Sim*.

1. Ir para **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Downloadable Product Option]** > **[!UICONTROL Order Item status for Download]** e verifique se está definido como *&quot;Faturado&quot;*.
1. Na loja, faça logon como cliente.

   * Adicione qualquer produto para download e um produto simples ao carrinho.
   * Uso [!DNL Braintree Pay] para fazer o pedido usando a opção cartão.

1. Ir para **[!UICONTROL My Orders]** e verificar se a fatura é criada automaticamente para o pedido e se ambos os status do item são *&quot;Faturado&quot;*.
1. Ir para **[!UICONTROL My Downloadable Products]** e observe que o link de download ainda não está disponível.
1. Em Admin, vá para esse pedido e crie uma remessa para ele.
1. Na loja, acesse **[!UICONTROL My Downloadable Products]** e observe que o link de download agora está disponível.

<u>Resultados esperados</u>:

O link de download está disponível quando o status do produto baixável é *&quot;Faturado&quot;*.

<u>Resultados reais</u>:

O link de download não está disponível mesmo quando o status do produto baixável é *&quot;Faturado&quot;*. Ela só estará disponível depois que uma remessa for criada para o produto físico.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.
