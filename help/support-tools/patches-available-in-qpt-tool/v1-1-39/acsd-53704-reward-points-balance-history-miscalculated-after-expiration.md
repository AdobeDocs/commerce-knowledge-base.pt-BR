---
title: "ACSD-53704: histórico de saldo de pontos de premiação calculado incorretamente após a expiração"
description: Aplique o patch ACSD-53704 para corrigir o problema do Adobe Commerce em que o histórico de saldo de pontos de premiação é calculado incorretamente após a data de expiração dos pontos de premiação.
feature: Rewards
role: Admin, Developer
exl-id: 5300cc22-0425-4467-b1e2-8bd799afb5fd
source-git-commit: dccb8dde1666fa0c72c7c94cd94c82daddaadc54
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---

# ACSD-53704: histórico de saldo de pontos de premiação calculado incorretamente após a expiração

O patch ACSD-53704 corrige o problema em que o histórico de saldo de pontos de premiação é calculado incorretamente após a data de expiração dos pontos de premiação. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.39 está instalado. A ID do patch é ACSD-53704. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O histórico de saldo de pontos de premiação é calculado incorretamente após a data de expiração dos pontos de premiação.

<u>Etapas a serem reproduzidas</u>:

1. Crie um cliente na loja.
1. Adicione pontos de premiação para o cliente com datas de expiração diferentes.
1. Verifique a tabela `magento_reward_history` e defina a data de expiração do último registro de pontos de premiação para uma data passada:

   ```
   UPDATE magento_reward_history SET expired_at_static = '2023-08-24 10:47:38' WHERE history_id = 3;
   ```

1. Verifique a grade do histórico de premiações em **[!UICONTROL Admin]** > **[!UICONTROL Customers]** > **[!UICONTROL All Customers]** > **[!UICONTROL Edit customer]** > **[!UICONTROL Reward points]** > **[!UICONTROL Reward Points History]** e **[!UICONTROL Reward Points Balance]**.

<u>Resultados esperados</u>:

O saldo de pontos de premiação mostra apenas os pontos não expirados.

<u>Resultados reais</u>:

O saldo de pontos de premiação reflete a quantidade que inclui os pontos expirados.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] versão: uma nova ferramenta para autoatender patches de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando o [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
