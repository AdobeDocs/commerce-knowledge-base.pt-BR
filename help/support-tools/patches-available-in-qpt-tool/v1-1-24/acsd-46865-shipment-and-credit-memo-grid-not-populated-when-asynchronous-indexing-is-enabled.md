---
title: '"ACSD-46865: [!UICONTROL shipment] e [!UICONTROL credit memo] não preenchido quando [!UICONTROL asynchronous indexing] está habilitado'''
description: Aplique o patch ACSD-46865 para corrigir o problema do Adobe Commerce em que [!UICONTROL shipment] e [!UICONTROL credit memo] as grades não são preenchidas quando [!UICONTROL asynchronous indexing] está ativado.
exl-id: 056177a8-42f0-4138-8c04-5b037d25dfd0
feature: Cache, Orders, Returns, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# ACSD-46865: [!UICONTROL shipment] e [!UICONTROL credit memo] não preenchido quando [!UICONTROL asynchronous indexing] está ativado

O patch ACSD-46865 corrige o problema em que [!UICONTROL shipment] e [!UICONTROL credit memo] as grades não são preenchidas quando [!UICONTROL asynchronous indexing] está ativado. Este patch está disponível quando a variável [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.24 está instalado. A ID do patch é ACSD-46865. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.5-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

[!UICONTROL Shipment] e [!UICONTROL credit memo] as grades não são preenchidas quando [!UICONTROL asynchronous indexing] está ativado.

<u>Etapas a serem reproduzidas</u>:

1. No [!DNL Commerce] Administrador, acesse **[!UICONTROL Set Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL Developer]** > **[!UICONTROL Grid Settings]** > **[!UICONTROL Asynchronous indexing Enable]** = *SIM*.
2. Mais uma vez, vá para **[!UICONTROL Set Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Sales]** > **[!UICONTROL Orders]** > **[!UICONTROL Invoices]** > **[!UICONTROL Shipments]** > **[!UICONTROL Credit Memos Archiving]** > **[!UICONTROL Enable Archiving]** = *[!UICONTROL YES]*.
3. Limpar cache de configuração.
4. Faça um novo pedido de um produto simples.
5. Execute o cron.
6. Abra o pedido no [!UICONTROL Commerce] Administrador acessando **[!UICONTROL Sales]** > **[!UICONTROL Orders]** e gerar uma NFF e um aviso de crédito.
7. Mover a ordem para [!UICONTROL Archive].
8. Criar outro pedido para um produto simples.
9. Execute o cron.
10. Vá para a nova ordem e gere uma nova entrega, uma NFF e um aviso de crédito.
11. Execute o cron.
12. Verifique a [!UICONTROL shipments], [!UICONTROL invoices], e [!UICONTROL credit memo] grades no administrador.

<u>Resultados esperados</u>:

Novo [!UICONTROL shipment], [!UICONTROL invoice] e [!UICONTROL credit memo] são exibidos.

<u>Resultados reais</u>:

Novo [!UICONTROL shipment], [!UICONTROL invoice], e [!UICONTROL credit memo] não são exibidos.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.
