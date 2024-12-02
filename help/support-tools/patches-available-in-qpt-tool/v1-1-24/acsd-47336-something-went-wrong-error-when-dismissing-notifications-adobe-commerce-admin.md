---
title: 'ACSD-47336: erro [!UICONTROL Something went wrong] ao descartar notificações no Adobe Commerce Admin'
description: Aplique o patch ACSD-47336 para corrigir o problema do Adobe Commerce em que o usuário vê o erro [!UICONTROL Something went wrong] ao dispensar notificações no  [!DNL Commerce] Administrador.
exl-id: 7561f055-ce04-4a49-8c58-271c24420a60
feature: Admin Workspace
role: Admin
source-git-commit: 8b6bf1cdada7edb0cdb0bb3e90ed15ee8cebf77e
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---

# ACSD-47336: erro _[!UICONTROL Something went wrong]_ao descartar notificações no Adobe Commerce Admin

O patch ACSD-47336 corrige o problema em que o usuário vê o erro _[!UICONTROL Something went wrong]_ao dispensar notificações no administrador [!DNL Commerce]. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.24 está instalado. A ID do patch é ACSD-47336. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação): 2.4.5

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação): 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O usuário vê o erro _[!UICONTROL Something went wrong]_ao dispensar notificações no Administrador [!DNL Commerce].

<u>Etapas a serem reproduzidas</u>:

1. Executar uma operação em massa (por exemplo, atualização em massa dos atributos do produto na grade de produtos).
1. Conclua a operação (por exemplo, execute `bin/magento queue:consumer:start product_action_attribute.update`).
1. Atualize a página de Administrador [!DNL Commerce], expanda a seção de notificação de administrador e clique no link **[!UICONTROL Dismiss All Completed Tasks]**.

<u>Resultados esperados</u>:

O erro _[!UICONTROL Something went wrong]_não deve ser exibido ao limpar as tarefas concluídas.

<u>Resultados reais</u>:

O erro _[!UICONTROL Something went wrong]_é exibido.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] versão: uma nova ferramenta para autoatender patches de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando o [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
