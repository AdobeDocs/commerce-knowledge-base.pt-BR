---
title: "ACSD-52824: Métodos de pagamento desativados exibidos para clientes da empresa"
description: Aplique o patch ACSD-52824 para corrigir o problema do Adobe Commerce em que [!DNL PayPal Express], [!DNL Google Pay], and [!DNL Apple Pay] os métodos de pagamento são exibidos para clientes da empresa apesar de estarem desativados nas configurações da empresa.
feature: Payments, B2B, Shopping Cart
role: Admin, Developer
exl-id: 03496fb1-d492-4f02-9cdc-466cb571a2eb
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---

# ACSD-52824: Métodos de pagamento desativados exibidos para clientes da empresa

O patch ACSD-52824 corrige o problema em que [!DNL PayPal Express], [!DNL Google Pay], e [!DNL Apple Pay] os métodos de pagamento são exibidos para clientes da empresa apesar de estarem desativados nas configurações da empresa. Este patch está disponível quando a variável [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.45 está instalado. A ID do patch é ACSD-52824. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Métodos de pagamento desativados são exibidos para clientes da empresa.

<u>Etapas a serem reproduzidas</u>:

1. Configurar e habilitar [!DNL PayPal Express Checkout]. Navegue até **[!UICONTROL Basic Settings]** > selecionar **[!DNL PayPal Express Checkout]** e defina a opção para **[!UICONTROL Display on Shopping Cart]** para *Sim*.
1. Configurar [!DNL Braintree] e habilitar [!DNL Apple Pay] e [!DNL Google Pay] até [!DNL Braintree].
1. Navegue até **[!UICONTROL Customers]** > **[!UICONTROL Companies]** e criar uma nova empresa.
1. Clique em **[!UICONTROL Advanced Settings]**, localize o **[!UICONTROL Applicable Payment Methods]** e escolha **[!UICONTROL Selected Payment Methods]**.
1. Em **[!UICONTROL Selected Payment Methods]**, escolha os métodos de pagamento ativados e não associados a *[!DNL PayPal Express Checkout]*, *[!DNL Apple Pay]* ou *[!DNL Google Pay]*. Por exemplo, selecione **[!UICONTROL Check/Money Order]**.
1. Após selecionar os métodos de pagamento apropriados, crie um novo cliente e associe-o à empresa criada anteriormente.
1. Faça logon com a conta de cliente associada à empresa e prossiga para adicionar itens ao carrinho.
1. Preste atenção ao minicarrinho, carrinho de compras e à etapa de pagamento durante o processo de finalização.

<u>Resultados esperados</u>:

Opções de pagamento de [!DNL PayPal] e [!DNL Braintree] não estão visíveis no minicarrinho e no carrinho de compras.

<u>Resultados reais</u>:

Opções de pagamento de [!DNL PayPal] e [!DNL Braintree] permanecem visíveis no minicarrinho e no carrinho de compras.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.
