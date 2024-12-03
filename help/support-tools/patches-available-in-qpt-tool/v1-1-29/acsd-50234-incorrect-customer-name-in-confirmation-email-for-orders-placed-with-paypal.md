---
title: 'ACSD-50234: Nome de cliente incorreto no email de confirmação para pedidos feitos usando  [!DNL PayPal]'
description: Aplique o patch ACSD-50234 para corrigir o problema do Adobe Commerce em que o nome do cliente é exibido incorretamente no email de confirmação para pedidos feitos usando o  [!DNL PayPal].
exl-id: b2e9c25a-5dd5-4b37-81e3-ca960078da77
feature: Admin Workspace, Communications, Orders, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---

# ACSD-50234: Nome de cliente incorreto no email de confirmação para pedidos feitos usando [!DNL PayPal]

O patch ACSD-50234 corrige o problema em que o nome do cliente é exibido incorretamente no email de confirmação para pedidos feitos usando o [!DNL PayPal]. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.29 está instalado. A ID do patch é ACSD-50234. Observe que o problema foi corrigido no Adobe Commerce 2.4.5.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.7 - 2.4.4-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O email de confirmação para pedidos feitos usando [!DNL PayPal] mostra o nome de cliente errado.

<u>Etapas a serem reproduzidas</u>

1. Habilitar **[!UICONTROL PayPal Express Checkout]**.
1. Navegue até o front-end como um convidado.
1. Adicione produtos ao carrinho.
1. Check-out usando **[!UICONTROL PayPal Express Checkout]** como método de pagamento.
1. Verifique o email de confirmação do pedido.

<u>Resultados esperados</u>

O email de confirmação do pedido, o email da fatura e todos os emails relacionados à remessa são endereçados ao nome do cliente.

<u>Resultados reais</u>

O email de confirmação do pedido, o email de fatura e todos os emails relacionados à remessa são endereçados ao *Convidado*.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] versão: uma nova ferramenta para autoatender patches de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando o [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
