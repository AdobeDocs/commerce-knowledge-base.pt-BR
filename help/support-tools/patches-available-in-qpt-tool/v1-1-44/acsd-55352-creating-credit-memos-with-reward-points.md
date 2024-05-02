---
title: "ACSD-55352: Criação de avisos de crédito com pontos de recompensa"
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

O patch ACSD-55352 corrige o problema em que, após criar um memorando de crédito parcial com pontos de premiação do cliente, o status do pedido muda para *fechado* as opções e de aviso de crédito desaparecem da página pedido de administrador. Este patch está disponível quando a variável [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.44 está instalado. A ID do patch é ACSD-55352. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Depois de criar um aviso de crédito parcial com pontos de premiação do cliente, o status do pedido muda para *fechado* as opções e de aviso de crédito desaparecem da página pedido de administrador.

<u>Etapas a serem reproduzidas</u>:

1. Faça logon no Administrador do Adobe Commerce.
2. Ir para **[!UICONTROL Stores]** > **[!UICONTROL Other Setting]** > **[!UICONTROL Reward Exchange Rates]** > **[!UICONTROL Add New Rate]**.
3. Adicione duas taxas:
   * *[!UICONTROL First]*:
      * *[!UICONTROL Direction]* = *Aponta para Moeda*
      * *[!UICONTROL Rate]* = *100*
      * *[!UICONTROL Upper Boundary]* = *100*
   * *[!UICONTROL Second]*:
      * *[!UICONTROL Direction]* = *Moeda para pontos*
      * *[!UICONTROL Rate]* = *100*
      * *[!UICONTROL Upper Boundary]* = *100*
4. Crie um produto simples com o preço de *$ 100* e com *Qtd* : *100*.
5. Crie um cliente na loja.
6. Ir para o back-end novamente: **[!UICONTROL Customers]** > **[!UICONTROL All Customers]** > **[!UICONTROL Edit]** > **[!UICONTROL Reward Points]** > **[!UICONTROL Update Points]** > Adicionar *100* e salve o cliente.
7. Acesse a loja e faça logon como o cliente criou anteriormente.
8. Adicionar o produto ao carrinho com *Qtd* : *10*.
9. Ir para **[!UICONTROL Checkout]** e use o disponível *100* pontos de premiação quando solicitado e colocar o pedido.
10. Ir para **[!UICONTROL Admin]** > **[!UICONTROL Sales]** > **[!UICONTROL Orders]** > **[!UICONTROL Invoice]** e enviar essa ordem.
11. Ir para [!UICONTROL Credit Memo] e atualize o *Qtde. para Reembolso* para *8*.
12. Marque a caixa **[!UICONTROL Refund Reward Points]** e clique em **[!UICONTROL Refund offline]**.
13. Tente reembolsar os outros dois produtos restantes do pedido, usando o [!UICONTROL Credit Memo].

<u>Resultados esperados</u>:

* O administrador cria [!UICONTROL Credit Memo] para devolver os dois produtos restantes.
* O status do pedido é *Concluído*.

<u>Resultados reais</u>:

* Não é possível criar mais [!UICONTROL Credit Memo].
* O status do pedido é *Fechado*.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.
