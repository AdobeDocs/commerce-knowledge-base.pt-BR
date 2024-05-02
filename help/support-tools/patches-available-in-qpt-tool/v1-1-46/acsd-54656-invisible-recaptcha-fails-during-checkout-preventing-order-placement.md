---
title: Invisível [!DNL reCAPTCHA] falha durante o check-out, impedindo a realização do pedido
description: Aplique o patch ACSD-54656 para corrigir o problema do Adobe Commerce em que o invisível [!DNL reCAPTCHA] não está funcionando corretamente durante o check-out, o que está impedindo a realização de um pedido.
feature: Checkout, Gift
role: Admin, Developer
exl-id: dc26659e-ca34-461e-af91-b230c5afa919
source-git-commit: fe6269ac042326a85a2cab5ccf834ac3eff1c166
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---

# ACSD-54656: Invisível [!DNL reCAPTCHA] não está funcionando corretamente durante o check-out, o que está impedindo a realização de um pedido.

O patch ACSD-54656 corrige o problema em que o invisível [!DNL reCAPTCHA] não está funcionando corretamente durante o check-out, o que está impedindo a realização de um pedido. Este patch está disponível quando a variável [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.46 está instalado. A ID do patch é ACSD-54656. Observe que o problema foi corrigido no Adobe Commerce 2.4.6.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p4

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5 - 2.4.5-p5

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Invisível [!DNL reCAPTCHA] não está funcionando corretamente durante o check-out, o que está impedindo a realização de um pedido.

<u>Etapas a serem reproduzidas</u>:

1. Habilitar qualquer tipo de [!DNL reCAPTCHA] para cartão-presente no [!UICONTROL Checkout] página.
1. Adicionar produto ao carrinho e ir para a **[!UICONTROL Checkout]** página.
1. Expanda o formulário de cartão-presente e preencha um cupom de cartão-presente válido.
1. Clique em **[!UICONTROL See balance and apply]** botão.

<u>Resultados esperados</u>:

O cartão-presente foi aplicado com êxito.

<u>Resultados Reais</u>:

A mensagem de erro é exibida: *[!DNL reCAPTCHA]falha na validação, tente novamente*.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.
