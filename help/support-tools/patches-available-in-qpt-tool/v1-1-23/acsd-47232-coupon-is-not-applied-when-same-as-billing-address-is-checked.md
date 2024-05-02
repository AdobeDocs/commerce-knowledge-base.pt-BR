---
title: '"ACSD-47232: o cupom não é aplicado quando [!UICONTROL Same as Billing Address] está marcado'''
description: Aplique o patch ACSD-47232 para corrigir o problema do Adobe Commerce em que o cupom não é aplicado quando [!UICONTROL Same as Billing Address] está marcado.
exl-id: 29b95a0b-8792-4830-a1e5-ce977f8453ec
feature: Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# ACSD-47232: o cupom não é aplicado quando [!UICONTROL Same as Billing Address] está marcado

O patch ACSD-47232 corrige o problema em que o cupom não é aplicado quando **[!UICONTROL Same as Billing Address]** está marcado. Este patch está disponível quando a variável [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.23 está instalado. A ID do patch é ACSD-47232. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O cupom não é aplicado quando **[!UICONTROL Same as Billing Address]** está marcado.

<u>Etapas a serem reproduzidas</u>:

1. Instale o Adobe Commerce.
1. Criar um produto simples com peso = *8*.
1. Crie um novo cliente com faturamento e endereço de entrega padrão.
1. Crie uma regra de preço de carrinho com um cupom.
   * Entrada **[!UICONTROL Conditions]** seções, adicionar *Peso Total igual ou maior que 5*
1. Tente criar um novo pedido no [!UICONTROL Commerce] Admin.
   * Use o cliente criado agora mesmo
   * Adicionar um produto
   * Tente aplicar o cupom

<u>Resultados esperados</u>:

Cupom aplicado.

<u>Resultados reais</u>:

Você recebe um erro semelhante ao seguinte: *O código do cupom 123 não é válido. Verifique o código e tente novamente.*

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.
