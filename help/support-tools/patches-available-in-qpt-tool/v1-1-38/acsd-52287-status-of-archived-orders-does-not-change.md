---
title: "ACSD-52287: o status dos pedidos arquivados não é alterado"
description: Aplique o patch ACSD-52287 para corrigir o problema do Adobe Commerce em que o status dos pedidos arquivados não muda de *concluído* para *fechado* na grade após o envio do memorando de crédito.
feature: Orders, Checkout
role: Admin, Developer
exl-id: c88c5c87-eec7-4105-9e4e-815d0888a34b
source-git-commit: 178023177975f210ebf7dd07e8c75cfe3ac89ff1
workflow-type: tm+mt
source-wordcount: '459'
ht-degree: 0%

---

# ACSD-52287: o status dos pedidos arquivados não é alterado

O patch ACSD-52287 corrige o problema em que o status dos pedidos arquivados não muda de *concluído* para *fechado* na grade após o envio do memorando de crédito. Este patch está disponível quando a variável [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.38 está instalado. A ID do patch é ACSD-52287. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O status dos pedidos arquivados não muda de *concluído* para *fechado* na grade após o envio do memorando de crédito.

<u>Etapas a serem reproduzidas</u>:

1. Configurar *[!UICONTROL Asynchronous Indexing]*.
   * Na barra lateral Admin, acesse **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]**.
   * No painel esquerdo, expanda a **[!UICONTROL Advanced]** e escolha **[!UICONTROL Developer]** por baixo.
   * Expanda a **[!UICONTROL Grid Settings]** seção.
   * Definir *[!UICONTROL Asynchronous indexing]* para *Sim*.
   * Clique em **[!UICONTROL Save Config]**.
1. Configure o *[!UICONTROL Order Archive]*.
   * Na barra lateral Admin, acesse **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]**.
   * No painel esquerdo, expanda a **[!UICONTROL Sales]** e escolha **[!UICONTROL Sales]** por baixo.
   * Expanda a **[!UICONTROL Orders, Invoices, Shipments, Credit Memos Archiving]** seção.
   * Definir *[!UICONTROL Enable Archiving]* para *Sim* (Deixe restante das configurações como padrão).
   * Clique em **[!UICONTROL Save Config]**.
1. Coloque um pedido no front-end.
1. Execute o [!DNL cron]  para que a ordem apareça na caixa *[!UICONTROL Admin Order Grid]*.
1. Faturar e Enviar a ordem para atualizar o status da ordem para *Concluído*.
1. Execute o [!DNL cron]  para atualizar o *[!UICONTROL Sales Order Grid]* com o status do pedido mais recente.
1. Arquivar o pedido.
1. Vá para a *[!UICONTROL Archived order grid]*.
1. Abra a ordem arquivada e devolva-a off-line criando uma [!UICONTROL Credit Memo] para tornar o [!UICONTROL Order status]: *Fechado*.
1. Execute o [!DNL cron] por algumas vezes.
1. Verifique a *[!UICONTROL Archived order grid]* para o novo status do pedido.

<u>Resultados esperados</u>:

A ordem é exibida como *Fechado*.

<u>Resultados reais</u>:

A ordem é exibida como *Concluído*.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.
