---
title: 'ACSD-48773: modelo de email de pontos de recompensa retirado da loja errada'
description: Aplique o patch ACSD-48773 para corrigir o problema do Adobe Commerce em que o modelo de email de pontos de premiação é retirado da loja errada.
exl-id: 96dda97c-5177-4883-ad2b-709928cb5f4d
feature: Admin Workspace, Communications, Marketing Tools, Orders, Personalization, Rewards
role: Admin
source-git-commit: 8b6bf1cdada7edb0cdb0bb3e90ed15ee8cebf77e
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 0%

---

# ACSD-48773: modelo de email de pontos de recompensa retirado da loja errada

O patch ACSD-48773 corrige o problema em que o modelo de email de pontos de premiação é retirado do armazenamento errado. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.26 está instalado. A ID do patch é ACSD-48773. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2 - 2.4.6

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A reindexação do preço do produto não funciona se o produto do pacote não estiver atribuído a nenhum site.

<u>Etapas a serem reproduzidas</u>:

1. Crie 2 sites, 2 lojas e 2 visualizações de loja.
1. Vá para **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Product Reviews]** e habilite **[!UICONTROL Reviews]**.
1. Vá para **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Store Email Addresses]**.
Alterne para **[!DNL default website scope]** e defina o endereço **[!UICONTROL Customer Support Sender Email]**, (Por exemplo: *support_base@example.com*).
Alterne para **[!DNL second website scope]** e defina o endereço **[!UICONTROL Customer Support Sender Email]** com outro valor (Por exemplo: *support_second@example.com*).
1. Vá para **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Customer Configuration]** > **[!UICONTROL Account Sharing Options]** > **[!UICONTROL Share Customer Accounts]** e defina **[!UICONTROL Share Customer Accounts]** = *Por Site*.
1. Em **[!UICONTROL Reward Points]**, defina o seguinte:
   **[!UICONTROL Enable Reward Points Functionality]** = *Sim*
   **[!UICONTROL Enable Reward Points Functionality on Storefront]** = *Sim*
   **[!UICONTROL Actions for Acquiring Reward Points by Customers]** > **[!UICONTROL Review Submission]** e conjunto **[!UICONTROL Review Submission]** = *150*
   **[!UICONTROL Email Notification Settings]** > **[!UICONTROL Email Sender]** e definir **[!UICONTROL Email Sender]** = *Suporte ao Cliente*
1. Vá para **[!UICONTROL Stores]** > **[!UICONTROL Other Settings]** > **[!UICONTROL Reward Exchange Rates]** e configure as taxas de câmbio para o segundo site para **[!UICONTROL Points/Currency]** e **[!UICONTROL Currency/Points]**.
1. Crie uma conta de cliente no segundo site.
1. Faça logon como o cliente no segundo site.
1. Habilite **[!UICONTROL Subscribe]** para **[!UICONTROL Balance Updates]**.
1. Envie uma análise do produto.
1. Vá para **[!UICONTROL Marketing]** > **[!UICONTROL User Content]** > **[!UICONTROL Pending Reviews]**.
1. Alterar o status da nova revisão para ***[!UICONTROL Approved]*** e **[!UICONTROL Save]**.
1. Aguarde a chegada do email.

<u>Resultados esperados</u>:

O email de atualização dos pontos de premiação deve ter sido enviado pelo remetente do email configurado no escopo do segundo site.

<u>Resultados reais</u>:

O email de atualização de pontos de premiação foi enviado pelo remetente de email configurado no escopo padrão do site.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] versão: uma nova ferramenta para autoatender patches de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando o [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
