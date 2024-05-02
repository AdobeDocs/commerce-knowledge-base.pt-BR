---
title: "ACSD-47520: os clientes perdem pontos de recompensa quando um memorando de crédito é criado"
description: Aplique o patch ACSD-47520 para corrigir o problema do Adobe Commerce em que os clientes perdem pontos de recompensa quando um memorando de crédito é criado.
exl-id: 748b4e05-981d-49f6-a4f5-b121d57085f4
feature: Admin Workspace, Cache, Orders, Rewards, Returns
role: Admin
source-git-commit: 3eeb86c2644f8a04ddcf5e205bc400d2ca9969af
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# ACSD-47520: os clientes perdem pontos de premiação quando um memorando de crédito é criado

O patch ACSD-47520 corrige o problema em que os clientes perdem pontos de recompensa quando um memorando de crédito é criado. Este patch está disponível quando a variável [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.25 está instalado. A ID do patch é ACSD-47520. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**
* Adobe Commerce (todos os métodos de implantação) 2.4.5

**Compatível com as versões do Adobe Commerce:**
* Adobe Commerce (todos os métodos de implantação) 2.4.0 - 2.4.5-p4

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os clientes perdem pontos de premiação quando um memorando de crédito é criado.

<u>Etapas a serem reproduzidas</u>:

1. Acesse o Administrador do Adobe Commerce > **[!UICONTROL Store]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Reward Points]**.
1. Altere a configuração:
   * **[!UICONTROL Enable Reward Points Functionality]** = _Sim_
   * **[!UICONTROL Enable Reward Points Functionality on Storefront]** = _Sim_
   * **[!UICONTROL Customers May See Reward Points History]** = _Sim_
   * **[!UICONTROL Refund Reward Points Automatically]** = _Não_
   * **[!UICONTROL Deduct Reward Points from Refund Amount Automatically]** = _Sim_
1. Acesse o Admin > **[!UICONTROL Store]** > **[!UICONTROL Other Settings]** > **[!UICONTROL Reward Exchange Rates]** e clique em **[!UICONTROL Add New Rate]**.
1. Adicione uma nova taxa (1:1) e limpe o cache.
1. Crie um cliente e adicione 10 pontos de premiação a esta conta.
1. Acesse o Admin > **[!UICONTROL Sales]** > **[!UICONTROL Orders]** > **[!UICONTROL Create New Order]** > Selecione o cliente criado na etapa anterior.
1. Selecione qualquer produto cujo preço seja maior que os pontos de premiação.
1. Fazer um pedido por meio de qualquer método de pagamento e dos pontos de premiação.
1. Criar uma fatura para o pedido.
1. Criar um memorando de crédito, mas não reembolsar os pontos de premiação.

<u>Resultados esperados</u>:

* O Administrador pode reembolsar os pontos de premiação.

* O status do pedido será fechado.

<u>Resultados reais</u>:

* Não há como reembolsar os pontos de recompensa.

* O status do pedido é **[!UICONTROL Completed]**.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.
