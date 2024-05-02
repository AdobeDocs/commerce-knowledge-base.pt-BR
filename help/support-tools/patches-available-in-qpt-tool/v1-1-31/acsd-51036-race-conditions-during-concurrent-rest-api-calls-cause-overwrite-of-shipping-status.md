---
title: "ACSD-51036: as condições de corrida durante chamadas de API REST simultâneas resultam em uma substituição do status do envio"
description: Aplique o patch ACSD-51036 para corrigir o problema do Adobe Commerce em que há condições de corrida durante chamadas de API REST simultâneas, resultando em uma substituição do status de envio na tabela itens solicitados.
exl-id: 12d90de7-fe5c-4fcc-b84a-d420dcd871ca
feature: REST, Orders, Shipping/Delivery
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---

# ACSD-51036: As condições de corrida durante chamadas de API REST simultâneas resultam em uma substituição do status de entrega na tabela itens solicitados

O patch ACSD-51036 corrige o problema em que as condições de corrida durante chamadas de API REST simultâneas resultam em uma substituição do status de envio na tabela itens solicitados. Este patch está disponível quando a variável [!DNL Quality Patches Tool (QPT)] O 1.1.31 está instalado. A ID do patch é ACSD-51036. Observe que o problema foi corrigido no Adobe Commerce 2.4.5.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.6

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

As condições de corrida durante chamadas de API REST simultâneas resultam em uma substituição do status da remessa na tabela itens solicitados.

<u>Etapas a serem reproduzidas</u>:

1. Criar um pedido com dois itens.
1. Item de NFF A.
1. Envie solicitação de reembolso para o item A via REST API simultaneamente enquanto envia uma solicitação de entrega para o item B.
1. Vá para a ordem em **[!UICONTROL Admin Panel]**.

<u>Resultados esperados</u>

*[!UICONTROL Shipped 1]* O status deve estar presente para o item B na *[!UICONTROL Items]* tabela ordenada.

<u>Resultados reais</u>

*[!UICONTROL Shipped 1]* O status não está presente para o item B na *[!UICONTROL Items]* tabela ordenada.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.
