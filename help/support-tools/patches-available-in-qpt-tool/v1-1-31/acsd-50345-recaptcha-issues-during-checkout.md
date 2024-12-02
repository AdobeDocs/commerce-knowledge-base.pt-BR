---
title: 'ACSD-50345: problemas do reCAPTCHA durante a finalização'
description: Aplique o patch ACSD-50345 para corrigir o problema do Adobe Commerce em que as validações do reCAPTCHA v2 e v3 falham ao fazer pedidos e durante a finalização da compra.
exl-id: ac8c8130-0e4d-4610-9a55-afa779cce7a0
feature: Checkout, Orders
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---

# ACSD-50345: problemas do reCAPTCHA durante a finalização

O patch ACSD-50345 corrige o problema em que as validações do reCAPTCHA v2 e v3 falham ao fazer pedidos e durante a finalização. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.31 está instalado. A ID do patch é ACSD-50345. Observe que o problema foi parcialmente corrigido no Adobe Commerce 2.4.6 e está programado para ser completamente corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3 - 2.4.5-p2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

**Caso #1**

O Google reCAPTCHA v2 não é recarregado após o envio de um pagamento com falha.

<u>Etapas a serem reproduzidas</u>

1. Configurar **[!UICONTROL Google reCAPTCHA v2]** (*Não sou um robô*).
1. Habilitar o **[!UICONTROL reCAPTCHA]** para check-out.
1. Tente fazer um pedido sem clicar em **[!UICONTROL reCAPTCHA]**.
1. Depois que o usuário receber a mensagem de erro do reCAPTCHA ausente (*Falha na validação do reCAPTCHA, tente novamente*), clique no **[!UICONTROL reCAPTCHA]** e tente fazer um pedido.

<u>Resultados esperados</u>

O pedido não será feito com um reCAPTCHA incorreto.

<u>Resultados reais</u>

Ocorreu um erro - Falha na validação do *reCAPTCHA, tente novamente* e *Não existe esse carrinho com ID = 4*

**Caso #2**

O Google reCAPTCHA v3 Invisible não está funcionando no check-out e o pedido não pode ser feito. O evento `PlaceOrder` não foi acionado.

<u>Etapas a serem reproduzidas</u>

1. Configure o **[!UICONTROL reCAPTCHA v3 Invisible]** em **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Security]**.
1. Habilitar **[!UICONTROL reCAPTCHA v3 Invisible]** para check-out/inserção de um pedido na guia **[!UICONTROL Storefront]**.
1. Tente fazer um pedido usando o método de pagamento [!UICONTROL Check/Money order].

<u>Resultados esperados</u>

O pedido deve ser feito com o **[!UICONTROL reCAPTCHA]** ativado.

<u>Resultados reais</u>

Depois de clicar no botão **[!UICONTROL Place Order]**, ele é desativado e nada acontece.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] versão: uma nova ferramenta para autoatender patches de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando o [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
