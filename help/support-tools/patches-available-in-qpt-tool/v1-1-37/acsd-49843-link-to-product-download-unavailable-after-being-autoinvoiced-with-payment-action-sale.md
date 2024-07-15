---
title: "ACSD 49843: link de download do produto indisponível após ser faturado automaticamente com [!UICONTROL Payment Action] = [!UICONTROL Intent Sale]"
description: Aplique o patch ACSD-49843 para corrigir o problema do Adobe Commerce em que o link de download do produto fica indisponível depois que o item solicitado é faturado automaticamente por um método de pagamento online quando [!UICONTROL Payment Action] está definido como [!UICONTROL Intent Sale].
feature: Catalog Management, Configuration, Invoices, Orders, Storefront
role: Admin, Developer
exl-id: 4bfa3827-a2b1-4168-a39c-99c617ee4795
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '487'
ht-degree: 0%

---

# ACSD-49843: link de download do produto indisponível após ser faturado automaticamente com [!UICONTROL Payment Action] = [!UICONTROL Intent Sale]

O patch ACSD-49843 corrige o problema em que o link de download do produto fica indisponível depois que o item solicitado é faturado automaticamente por um método de pagamento online quando [!UICONTROL Payment Action] está definido como [!UICONTROL Intent Sale]. Este patch está disponível quando o [!DNL Quality Patches Tool (QPT)] 1.1.37 está instalado. A ID do patch é ACSD-49843. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.7 - 2.3.7-p4, 2.4.1 - 2.4.6-p2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O link de download do produto não estará disponível depois que o item solicitado for faturado automaticamente por um método de pagamento online quando [!UICONTROL Payment Action] estiver definido como [!UICONTROL Intent Sale].

<u>Etapas a serem reproduzidas</u>:

1. Faça logon no Administrador do Adobe Commerce e navegue até **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Configure Braintree]**.

   * Na lista suspensa [!UICONTROL Payment Action], selecione **[!UICONTROL Intent Sale]** e defina *[!UICONTROL Enable Card Payments]* como *Sim*.

1. Vá para **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Downloadable Product Option]** > **[!UICONTROL Order Item status for Download]** e verifique se está definido como *&quot;Faturado&quot;*.
1. Na loja, faça logon como cliente.

   * Adicione qualquer produto para download e um produto simples ao carrinho.
   * Use [!DNL Braintree Pay] para fazer o pedido usando a opção de cartão.

1. Vá para **[!UICONTROL My Orders]** e veja se a fatura é criada automaticamente para o pedido e se ambos os status dos itens são *&quot;Faturados&quot;*.
1. Vá para **[!UICONTROL My Downloadable Products]** e observe que o link de download ainda não está disponível.
1. Em Admin, vá para esse pedido e crie uma remessa para ele.
1. Na loja, vá para **[!UICONTROL My Downloadable Products]** e observe que o link de download agora está disponível.

<u>Resultados esperados</u>:

O link de download está disponível quando o status do produto para download é *&quot;Faturado&quot;*.

<u>Resultados reais</u>:

O link para download não está disponível mesmo quando o status do produto disponível para download indica *&quot;Faturado&quot;*. Ela só estará disponível depois que uma remessa for criada para o produto físico.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] versão: uma nova ferramenta para autoatender patches de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando o [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
