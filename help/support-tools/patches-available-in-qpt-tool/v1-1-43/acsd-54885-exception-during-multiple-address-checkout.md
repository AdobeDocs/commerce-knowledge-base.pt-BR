---
title: "ACSD-54885: exceção durante a finalização de vários endereços quando o administrador faz logon como cliente"
description: Aplique o patch ACSD-54885 para corrigir o problema do Adobe Commerce em que um erro ocorre durante a finalização de vários endereços quando o administrador está usando o *[!UICONTROL Login as Customer]* funcionalidade.
feature: Checkout
role: Admin, Developer
exl-id: 524ec96b-1465-4673-9fbe-1a9c086b7e87
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# ACSD-54885: exceção durante a finalização de vários endereços quando o administrador faz logon como cliente

O patch ACSD-54885 corrige o problema em que um erro ocorre durante a verificação de vários endereços quando o administrador está usando o *[!UICONTROL Login as Customer]* funcionalidade. Este patch está disponível quando a variável [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.43 está instalado. A ID do patch é ACSD-54885. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Ocorre um erro durante a finalização de vários endereços quando o administrador está usando o *[!UICONTROL Login as Customer]* funcionalidade.

<u>Etapas a serem reproduzidas</u>:

1. Assegure que *[!UICONTROL Login as Customer]* está ativado. Ir para **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Configurations]** > **[!UICONTROL Advanced]** > **[!UICONTROL Admin]** > **[!UICONTROL Admin Actions]** > **[!UICONTROL Logging]** > **[!UICONTROL Login as Customer]**.
1. Crie um produto simples.
1. Crie uma nova conta de cliente com um endereço.
1. Vá para a conta do cliente no back-end:

   * Vá para a **[!UICONTROL Account Information]** e defina *[!UICONTROL Allow remote shopping assistance]* = *Sim*.
   * Clique em **[!UICONTROL Login as Customer]**.

1. Adicione o produto ao carrinho e prossiga para *[!UICONTROL Checkout with multiple addresses]*.
1. Atualize a quantidade do produto.
1. Tente voltar para o carrinho de compras.

<u>Resultados esperados</u>:

Você pode atualizar o carrinho e usar a finalização de vários endereços.

<u>Resultados reais</u>:

Você recebe o seguinte erro ao voltar ao carrinho de compras.

```PHP
report.CRITICAL: Error: Call to a member function getCustomer() on null in magento2ee/app/code/Magento/LoginAsCustomerLogging/Observer/LogUpdateQtyObserver.php:88
```

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.
