---
title: 'ACSD-48362: o endereço de envio padrão é usado em vez de um novo.'
description: Aplique o patch ACSD-48362 para corrigir o problema do Adobe Commerce em que o endereço de envio padrão é usado em vez de um novo ao fazer um pedido usando uma cotação negociável.
exl-id: 52f518b6-6f73-42cc-ac1b-c893cd5007fa
feature: Admin Workspace, B2B, Orders, Shipping/Delivery
role: Admin
source-git-commit: 8b6bf1cdada7edb0cdb0bb3e90ed15ee8cebf77e
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 0%

---

# ACSD-48362: o endereço de envio padrão é usado em vez de um novo

O patch ACSD-48362 corrige o problema em que o endereço de envio padrão é usado em vez do endereço recém-adicionado ao fazer um pedido usando uma cotação negociável. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.27 está instalado. A ID do patch é ACSD-48362. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.1 - 2.4.6

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O endereço de entrega padrão é usado em vez do endereço de entrega recém-adicionado ao fazer um pedido usando uma cotação negociável.

<u>Etapas a serem reproduzidas</u>:

1. Habilite a cotação B2B navegando até **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL B2B features]** > **[!UICONTROL Enable company]** > **[!UICONTROL Enable B2B quote]**.
1. Efetue logon como usuário da empresa.
1. Adicione um produto ao carrinho.
1. Vá para a página do carrinho e solicite uma cotação.
1. Vá para a página **[!UICONTROL My Quotes]** do cliente e selecione a cotação que acabou de ser criada.
1. Acesse a seção **[!UICONTROL Shipping Information]** da página de cotação do cliente.
   * Clique em **[!UICONTROL Add New Address]**, preencha o formulário e salve o endereço (não selecione **[!UICONTROL Use as my default billing address]** ou **[!UICONTROL Use as my default shipping address]**).
1. Clique em **[!UICONTROL Send for Review]** na página de cotação do cliente.
1. Vá para o Administrador do Adobe Commerce como um usuário administrador, abra a cotação que acabou de ser criada e clique em **[!UICONTROL Send]**.
1. Agora vá para a página de cotação do cliente, atualize a página e clique em **[!UICONTROL Proceed to Checkout]**.
1. Na página de check-out, os dados mostram o endereço de envio padrão mesmo quando o novo endereço de envio é selecionado.
1. Clique em **[!UICONTROL Continue]** e faça o pedido.

<u>Resultados esperados</u>:

O pedido deve usar o novo endereço sem selecionar novamente o endereço de envio padrão na página de finalização da compra.

<u>Resultados reais</u>:

O pedido é feito com o endereço de entrega padrão.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem. 

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] versão: uma nova ferramenta para autoatender patches de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando o [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
