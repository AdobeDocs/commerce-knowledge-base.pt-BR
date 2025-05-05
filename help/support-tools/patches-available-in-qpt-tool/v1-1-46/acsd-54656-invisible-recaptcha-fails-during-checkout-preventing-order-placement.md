---
title: Invisível [!DNL reCAPTCHA] falha durante o check-out, impedindo o posicionamento do pedido
description: Aplique o patch ACSD-54656 para corrigir o problema do Adobe Commerce em que invisível [!DNL reCAPTCHA]  não está funcionando corretamente durante o check-out, o que está impedindo a inserção de um pedido.
feature: Checkout, Gift
role: Admin, Developer
exl-id: dc26659e-ca34-461e-af91-b230c5afa919
source-git-commit: fe6269ac042326a85a2cab5ccf834ac3eff1c166
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---

# ACSD-54656: [!DNL reCAPTCHA] invisível não está funcionando corretamente durante o check-out, o que está impedindo o posicionamento de um pedido.

O patch ACSD-54656 corrige o problema em que o invisível [!DNL reCAPTCHA] não está funcionando corretamente durante o check-out, o que impede a realização de um pedido. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.46 está instalado. A ID do patch é ACSD-54656. Observe que o problema foi corrigido no Adobe Commerce 2.4.6.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p4

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5 - 2.4.5-p5

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O invisível [!DNL reCAPTCHA] não está funcionando corretamente durante o check-out, o que está impedindo o posicionamento de um pedido.

<u>Etapas a serem reproduzidas</u>:

1. Habilite qualquer tipo de [!DNL reCAPTCHA] para cartão-presente na página [!UICONTROL Checkout].
1. Adicionar produto ao carrinho e ir para a página **[!UICONTROL Checkout]**.
1. Expanda o formulário de cartão-presente e preencha um cupom de cartão-presente válido.
1. Clique no botão **[!UICONTROL See balance and apply]**.

<u>Resultados Esperados</u>:

O cartão-presente foi aplicado com êxito.

<u>Resultados Reais</u>:

A mensagem de erro aparece: *[!DNL reCAPTCHA]falha na validação, tente novamente*.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] versão: uma nova ferramenta para autoatender patches de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando o [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
