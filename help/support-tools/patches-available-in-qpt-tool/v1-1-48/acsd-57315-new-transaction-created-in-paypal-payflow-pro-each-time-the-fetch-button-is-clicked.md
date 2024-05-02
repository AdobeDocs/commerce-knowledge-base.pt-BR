---
title: '"ACSD-57315: a nova transação é criada em [!DNL PayPal Payflow Pro] sempre que o botão buscar for clicado'''
description: Aplique o patch ACSD-57315 para corrigir o problema do Adobe Commerce em que uma nova transação é criada no [!DNL PayPal Payflow Pro] sempre que o botão buscar for clicado na tela exibir transação no [!UICONTROL Admin].
feature: Payments
role: Admin, Developer
source-git-commit: b7f85e4fdb7ef4a6328a1a411dac765dd8da083e
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# ACSD-57315: a nova transação é criada em [!DNL PayPal Payflow Pro] sempre que o botão buscar for clicado

O patch ACSD-57315 corrige o problema em que uma nova transação é criada no [!DNL PayPal Payflow Pro] sempre que o botão buscar for clicado na tela exibir transação no [!UICONTROL Admin]. Este patch está disponível quando a variável [!DNL Quality Patches Tool (QPT)] O 1.1.48 está instalado. A ID do patch é ACSD-57315. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.5.0.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4-p4

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2 - 2.4.6-p4

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Uma nova transação é criada em [!DNL PayPal Payflow Pro] sempre que o botão buscar for clicado na tela exibir transação no [!UICONTROL Admin].

<u>Etapas a serem reproduzidas</u>:

1. Configurar [!DNL PayPal Payflow Pro].
1. Defina o método de transação como *[!UICONTROL Sale]*.
1. Fazer um pedido usando *Cartão de crédito*.
1. Abrir a transação de [!UICONTROL Admin].
1. Clique no link **[!UICONTROL Fetch]** botão.
1. Marcar [!DNL PayPal] conta para transações relacionadas à ordem feita.

<u>Resultados esperados</u>:

Não é criada uma nova transação de pagamento.

<u>Resultados reais</u>:

Uma nova transação de pagamento é criada para um pedido que já foi pago.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.
