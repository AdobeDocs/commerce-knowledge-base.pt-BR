---
title: '"ACSD-47336: [!UICONTROL Something went wrong] erro ao dispensar notificações no Adobe Commerce Admin'''
description: Aplique o patch ACSD-47336 para corrigir o problema do Adobe Commerce em que o usuário vê [!UICONTROL Something went wrong] erro ao dispensar notificações no [!DNL Commerce] Admin.
exl-id: 7561f055-ce04-4a49-8c58-271c24420a60
feature: Admin Workspace
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---

# ACSD-47336: _[!UICONTROL Something went wrong]_erro ao dispensar notificações no Adobe Commerce Admin

O patch ACSD-47336 corrige o problema em que o usuário vê a variável _[!UICONTROL Something went wrong]_erro ao dispensar notificações no [!DNL Commerce] Admin. Este patch está disponível quando a variável [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.24 está instalado. A ID do patch é ACSD-47336. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação): 2.4.5

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação): 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O usuário vê _[!UICONTROL Something went wrong]_erro ao dispensar notificações no [!DNL Commerce] Admin.

<u>Etapas a serem reproduzidas</u>:

1. Executar uma operação em massa (por exemplo, atualização em massa dos atributos do produto na grade de produtos).
1. Concluir a operação (por exemplo, executar `bin/magento queue:consumer:start product_action_attribute.update`).
1. Atualize o [!DNL Commerce] Admin, expanda a seção notificação de administração e clique no link **[!UICONTROL Dismiss All Completed Tasks]** link.

<u>Resultados esperados</u>:

A variável _[!UICONTROL Something went wrong]_o erro não deve ser exibido ao limpar as tarefas concluídas.

<u>Resultados reais</u>:

A variável _[!UICONTROL Something went wrong]_é exibido.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.
