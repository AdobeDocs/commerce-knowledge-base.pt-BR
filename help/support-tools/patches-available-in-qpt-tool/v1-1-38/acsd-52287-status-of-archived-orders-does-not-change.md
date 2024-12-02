---
title: 'ACSD-52287: o status dos pedidos arquivados não é alterado'
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

O patch ACSD-52287 corrige o problema em que o status de pedidos arquivados não muda de *concluído* para *fechado* na grade após o envio do memorando de crédito. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.38 está instalado. A ID do patch é ACSD-52287. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O status dos pedidos arquivados não é alterado de *concluído* para *fechado* na grade após o envio do memorando de crédito.

<u>Etapas a serem reproduzidas</u>:

1. Configurar *[!UICONTROL Asynchronous Indexing]*.
   * Na barra lateral Admin, vá para **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]**.
   * No painel esquerdo, expanda a seção **[!UICONTROL Advanced]** e escolha **[!UICONTROL Developer]** abaixo.
   * Expanda a seção **[!UICONTROL Grid Settings]**.
   * Defina *[!UICONTROL Asynchronous indexing]* como *Sim*.
   * Clique em **[!UICONTROL Save Config]**.
1. Configure o *[!UICONTROL Order Archive]*.
   * Na barra lateral Admin, vá para **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]**.
   * No painel esquerdo, expanda a seção **[!UICONTROL Sales]** e escolha **[!UICONTROL Sales]** abaixo.
   * Expanda a seção **[!UICONTROL Orders, Invoices, Shipments, Credit Memos Archiving]**.
   * Definir *[!UICONTROL Enable Archiving]* como *Sim* (deixe o restante das configurações como padrão).
   * Clique em **[!UICONTROL Save Config]**.
1. Coloque um pedido no front-end.
1. Execute o [!DNL cron] para que a ordem apareça no *[!UICONTROL Admin Order Grid]*.
1. Faturar e Enviar a ordem para atualizar o status da ordem para *Concluído*.
1. Execute o [!DNL cron] para atualizar o *[!UICONTROL Sales Order Grid]* com o status de pedido mais recente.
1. Arquivar o pedido.
1. Vá para o *[!UICONTROL Archived order grid]*.
1. Abra o pedido arquivado e retorne o pedido offline criando um [!UICONTROL Credit Memo] para tornar o [!UICONTROL Order status]: *Fechado*.
1. Execute o [!DNL cron] por algumas vezes.
1. Verifique o *[!UICONTROL Archived order grid]* quanto ao novo status do pedido.

<u>Resultados esperados</u>:

A ordem é exibida como *Fechada*.

<u>Resultados reais</u>:

A ordem é exibida como *Concluída*.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] versão: uma nova ferramenta para autoatender patches de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando o [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
