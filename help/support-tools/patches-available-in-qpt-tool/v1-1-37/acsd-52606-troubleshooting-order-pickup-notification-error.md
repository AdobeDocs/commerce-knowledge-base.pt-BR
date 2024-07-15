---
title: 'ACSD-52606: Mensagem de erro exibida quando o usuário clica em "Notificar pedido pronto para retirada"'
description: Aplique o patch ACSD-52606 para corrigir o problema do Adobe Commerce em que uma mensagem de erro é exibida quando o usuário clica em **[!UICONTROL Notify Order is Ready for Pickup]**.
feature: Orders, User Account
role: Admin, Developer
exl-id: c3e69eb1-90bf-46cf-9b53-110e40e0c3c1
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# ACSD-52606: Mensagem de erro exibida quando o usuário clica em &quot;Notificar que a ordem está pronta para retirada&quot;

O patch ACSD-52606 corrige o problema em que uma mensagem de erro *Seu pedido não está pronto para retirada* é exibida quando o usuário clica em **[!UICONTROL Notify Order is Ready for Pickup]**. Este patch está disponível quando o [!DNL Quality Patches Tool (QPT)] 1.1.37 está instalado. A ID do patch é ACSD-52606. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.0 - 2.4.6-p2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Uma mensagem de erro *Seu pedido não está pronto para retirada* é exibida na tela quando o usuário clica em **[!UICONTROL Notify Order is Ready for Pickup]**.

<u>Pré-requisitos</u>:

Os módulos de inventário estão instalados.

<u>Etapas a serem reproduzidas</u>:

1. Instale a nova instância.
1. Criar uma nova fonte e estoque.
1. Atribua a nova origem ao site padrão.
1. Habilitar local de retirada para a origem recém-criada.
1. Vá para **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Delivery Methods]** > **[!UICONTROL In-Store Delivery]** e habilite **[!UICONTROL In-Store Delivery]**.
1. Crie um produto simples *Em Estoque* com *QTD=0* para todos os estoques e *[!UICONTROL Manage Stock = No]* e atribua-o a ambas as fontes.
1. Crie um pedido no front-end com o produto criado na etapa anterior, escolhendo *[!UICONTROL In-Store Pickup]* como método de entrega.
1. No Admin, vá para **[!UICONTROL Sales]** > **[!UICONTROL Orders]** > **[!UICONTROL Invoice that order]**.
1. Clique em **[!UICONTROL Notify order is ready for pickup]**.

<u>Resultados esperados</u>:

Você é notificado sem erros.

<u>Resultados reais</u>:

Você recebe a seguinte mensagem de erro: *Seu pedido não está pronto para retirada*.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] versão: uma nova ferramenta para autoatender patches de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando o [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
