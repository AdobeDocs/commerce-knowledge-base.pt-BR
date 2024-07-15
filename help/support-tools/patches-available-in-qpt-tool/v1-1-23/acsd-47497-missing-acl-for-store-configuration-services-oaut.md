---
title: "ACSD-47497: ACL ausente para Armazenamento/Configuração/Serviços [!UICONTROL OAuth]"
description: Aplique o patch ACSD-47497 para corrigir o problema do Adobe Commerce quando as permissões forem definidas para uma função específica e você não puder definir o acesso à seção de configuração.
exl-id: c13fd541-1379-4893-9190-9da1422b2b99
feature: Configuration, Identity Management, Services
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 0%

---

# ACSD-47497: ACL ausente para Armazenamento / Configuração / Serviços [!UICONTROL OAuth]

O patch ACSD-47497 resolve o problema em que a guia **[!UICONTROL Services]** não está visível na seção **[!UICONTROL Configuration]** no Administrador do Adobe Commerce. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.23 está instalado. A ID do patch é ACSD-47497. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**
* Adobe Commerce (todos os métodos de implantação) 2.4.4

**Compatível com as versões do Adobe Commerce:**
* Adobe Commerce (todos os métodos de implantação) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Quando permissões são definidas para uma função específica, você não pode definir o acesso a **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Services]** > **[!UICONTROL OAuth]**.

<u>Etapas a serem reproduzidas</u>:

1. Faça logon no Administrador do Adobe Commerce. Vá para **[!UICONTROL System]** > **[!UICONTROL Permissions]** > **[!UICONTROL User Roles]**.
1. Selecione **[!UICONTROL Role Resources]** na função de Administradores, defina **[!UICONTROL Resource Access]** em **[!UICONTROL Roles Resources]** como _Personalizado_ e marque todas as caixas de seleção. Selecione **[!UICONTROL Save Role]**.
1. Selecione **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Services]**. A seção de configuração **[!UICONTROL OAuth]** não está disponível.

<u>Resultados esperados</u>:

Em **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Services]** > **[!UICONTROL OAuth]**, a seção de configuração está visível.

<u>Resultados reais</u>:

Em **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Services]** > **[!UICONTROL OAuth]**, a seção de configuração está ausente.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] versão: uma nova ferramenta para autoatender patches de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando o [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
