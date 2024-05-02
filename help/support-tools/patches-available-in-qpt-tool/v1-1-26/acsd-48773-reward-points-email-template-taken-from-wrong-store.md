---
title: "ACSD-48773: modelo de email de pontos de recompensa retirado do armazenamento errado"
description: Aplique o patch ACSD-48773 para corrigir o problema do Adobe Commerce em que o modelo de email de pontos de premiação é retirado da loja errada.
exl-id: 96dda97c-5177-4883-ad2b-709928cb5f4d
feature: Admin Workspace, Communications, Marketing Tools, Orders, Personalization, Rewards
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 0%

---

# ACSD-48773: modelo de email de pontos de recompensa retirado da loja errada

O patch ACSD-48773 corrige o problema em que o modelo de email de pontos de premiação é retirado do armazenamento errado. Este patch está disponível quando a variável [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.26 está instalado. A ID do patch é ACSD-48773. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2 - 2.4.6

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A reindexação do preço do produto não funciona se o produto do pacote não estiver atribuído a nenhum site.

<u>Etapas a serem reproduzidas</u>:

1. Crie 2 sites, 2 lojas e 2 visualizações de loja.
1. Ir para **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Product Reviews]** e habilitar **[!UICONTROL Reviews]**.
1. Ir para **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Store Email Addresses]**.
Alterne para a **[!DNL default website scope]** e defina o **[!UICONTROL Customer Support Sender Email]** endereço, (Por exemplo: *support_base@example.com*).
Alterne para a **[!DNL second website scope]** e defina o **[!UICONTROL Customer Support Sender Email]** para outro valor (Por exemplo: *support_second@example.com*).
1. Ir para **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Customer Configuration]** > **[!UICONTROL Account Sharing Options]** > **[!UICONTROL Share Customer Accounts]** e defina **[!UICONTROL Share Customer Accounts]** = *Por site*.
1. Em **[!UICONTROL Reward Points]**, defina o seguinte:
   **[!UICONTROL Enable Reward Points Functionality]** = *Sim*
   **[!UICONTROL Enable Reward Points Functionality on Storefront]** = *Sim*
   **[!UICONTROL Actions for Acquiring Reward Points by Customers]** > **[!UICONTROL Review Submission]** e defina **[!UICONTROL Review Submission]** = *150*
   **[!UICONTROL Email Notification Settings]** > **[!UICONTROL Email Sender]** e defina **[!UICONTROL Email Sender]** = *Suporte ao cliente*
1. Ir para **[!UICONTROL Stores]** > **[!UICONTROL Other Settings]** > **[!UICONTROL Reward Exchange Rates]** e definir as taxas de câmbio para o segundo site para ambos **[!UICONTROL Points/Currency]** e **[!UICONTROL Currency/Points]**.
1. Crie uma conta de cliente no segundo site.
1. Faça logon como o cliente no segundo site.
1. Certifique-se de ativar **[!UICONTROL Subscribe]** para **[!UICONTROL Balance Updates]**.
1. Envie uma análise do produto.
1. Ir para **[!UICONTROL Marketing]** > **[!UICONTROL User Content]** > **[!UICONTROL Pending Reviews]**.
1. Alterar o status da nova revisão para ***[!UICONTROL Approved]*** e **[!UICONTROL Save]**.
1. Aguarde a chegada do email.

<u>Resultados esperados</u>:

O email de atualização dos pontos de premiação deve ter sido enviado pelo remetente do email configurado no escopo do segundo site.

<u>Resultados reais</u>:

O email de atualização de pontos de premiação foi enviado pelo remetente de email configurado no escopo padrão do site.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.
