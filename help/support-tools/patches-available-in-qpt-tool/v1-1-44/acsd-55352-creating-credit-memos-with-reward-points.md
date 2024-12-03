---
title: 'ACSD-55352: Criação de avisos de crédito com pontos de premiação'
description: Aplique o patch ACSD-55352 para corrigir o problema do Adobe Commerce em que, após criar um aviso de crédito parcial com pontos de premiação do cliente, o status do pedido muda para *fechado* e as opções de aviso de crédito desaparecem da página de pedido do administrador.
feature: Checkout, Orders
role: Admin, Developer
exl-id: 33ceb2e9-3cd5-4472-941a-e06c5c534f4a
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '480'
ht-degree: 0%

---

# ACSD-55352: Criação de avisos de crédito com pontos de premiação

O patch ACSD-55352 corrige o problema em que, após criar um memorando de crédito parcial com pontos de premiação do cliente, o status do pedido muda para *fechado* e as opções de memorando de crédito desaparecem da página de pedido de administrador. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.44 está instalado. A ID do patch é ACSD-55352. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Depois de criar um memorando de crédito parcial com pontos de premiação do cliente, o status do pedido muda para *fechado* e as opções de memorando de crédito desaparecem da página de pedido do administrador.

<u>Etapas a serem reproduzidas</u>:

1. Faça logon no Administrador do Adobe Commerce.
2. Vá para **[!UICONTROL Stores]** > **[!UICONTROL Other Setting]** > **[!UICONTROL Reward Exchange Rates]** > **[!UICONTROL Add New Rate]**.
3. Adicione duas taxas:
   * *[!UICONTROL First]*:
      * *[!UICONTROL Direction]* = *Pontos para Moeda*
      * *[!UICONTROL Rate]* = *100*
      * *[!UICONTROL Upper Boundary]* = *100*
   * *[!UICONTROL Second]*:
      * *[!UICONTROL Direction]* = *Moeda para Pontos*
      * *[!UICONTROL Rate]* = *100*
      * *[!UICONTROL Upper Boundary]* = *100*
4. Crie um produto simples com o preço de *$100* e com *Qtd* : *100*.
5. Crie um cliente na loja.
6. Acesse o back-end novamente: **[!UICONTROL Customers]** > **[!UICONTROL All Customers]** > **[!UICONTROL Edit]** > **[!UICONTROL Reward Points]** > **[!UICONTROL Update Points]** > Adicionar *100* e salve o cliente.
7. Acesse a loja e faça logon como o cliente criou anteriormente.
8. Adicionar o produto ao carrinho com *Qtd.*: *10*.
9. Vá para **[!UICONTROL Checkout]** e use os *100* pontos de premiação disponíveis, quando solicitado, e faça o pedido.
10. Vá para **[!UICONTROL Admin]** > **[!UICONTROL Sales]** > **[!UICONTROL Orders]** > **[!UICONTROL Invoice]** e envie esse pedido.
11. Vá para [!UICONTROL Credit Memo] e atualize a *Qtd. para Reembolso* para *8*.
12. Marque a caixa de seleção **[!UICONTROL Refund Reward Points]** e clique em **[!UICONTROL Refund offline]**.
13. Tente reembolsar os outros dois produtos restantes do pedido, usando o [!UICONTROL Credit Memo].

<u>Resultados esperados</u>:

* O Administrador cria [!UICONTROL Credit Memo] para retornar os dois produtos restantes.
* O status do pedido é *Concluído*.

<u>Resultados reais</u>:

* Não é possível criar mais [!UICONTROL Credit Memo].
* O status do pedido é *Fechado*.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] versão: uma nova ferramenta para autoatender patches de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando o [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
