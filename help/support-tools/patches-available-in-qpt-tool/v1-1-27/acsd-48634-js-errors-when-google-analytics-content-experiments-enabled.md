---
title: '"ACSD-48634: [!DNL JS] erros quando [!DNL Google Analytics Content Experiments] habilitado'''
description: Aplique o patch ACSD-48634 para corrigir [!DNL JS] erros em um [!DNL staging] atualizar página quando [!DNL Google Analytics Content Experiments] está ativado.
exl-id: 4a9f201d-eaf0-4e43-a1a1-0a9ffb0a2ead
feature: Catalog Management, Categories, Console, Page Content
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# ACSD-48634: [!DNL JS] erros quando [!DNL Google Analytics Content Experiments] habilitado

As correções de patch do ACSD-48634 [!DNL JS] erros em um [!DNL staging] atualizar página quando [!DNL Google Analytics Content Experiments] está ativado. Este patch está disponível quando a variável [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.27 está instalado. A ID do patch é ACSD-48634. Observe que o problema foi corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.7 - 2.4.6

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

[!DNL JS] erros ocorrem em um [!DNL staging] atualizar página quando [!DNL Google Analytics Content Experiments] está ativado.

<u>Etapas a serem reproduzidas</u>:

1. Entrada **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL All Stores]**, criar um site, loja e **[!UICONTROL Store View]**. Verifique se **[!UICONTROL Store View]** é *[!UICONTROL Enabled]*.
1. Configurar **[!DNL Configure Google Analytics]** acessando **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Google API]**:
   * Para **[!DNL Main]** e sites adicionais [!DNL scope]:
      * **[!UICONTROL Enabled]**: *[!UICONTROL Yes]*
      * **[!UICONTROL Account type]**: *[!UICONTROL Google Tag Manager]*
      * **[!UICONTROL Anonymize IP]**: *[!UICONTROL Yes]*
      * **[!UICONTROL Enable Content Experiments]**: *[!UICONTROL Yes]*
      * **[!UICONTROL Container Id]**: *[!UICONTROL (GTM container ID)]*
      * **[!DNL Uncheck]** *[!UICONTROL Use Default]* para outros campos, mas não os altere.
   * Para **[!DNL Default Config]** [!DNL scope]:
      * **[!UICONTROL Enabled]**: *[!UICONTROL Yes]*
      * **[!UICONTROL Account type]**: *[!UICONTROL Universal Analytics]*
      * **[!UICONTROL Account Number]**: *[!UICONTROL (Universal Analytics account number)]*
      * **[!UICONTROL Anonymize IP]**: *[!UICONTROL Yes]*
      * **[!UICONTROL Enable Content Experiments]**: *[!UICONTROL Yes]*
1. Desativar **[!DNL Configure Google Analytics]** em **[!DNL Default Config]** [!DNL scope] alterando **[!UICONTROL Enable]** de *[!UICONTROL Yes]* para *[!UICONTROL No]*. Certifique-se de não alterar mais nada!
1. Ir para **[!UICONTROL Catalog]** > **[!UICONTROL Categories]**.
1. Criar e editar qualquer **[!UICONTROL category]** e adicionar uma atualização agendada para ela:
   * Qualquer nome, data inicial futura, data final futura e qualquer alteração no **[!UICONTROL category]** ([!UICONTROL For Example]: *[!UICONTROL disable category]*).
1. Salve a atualização e verifique a [!DNL browser developer console] para erros.

<u>Resultados esperados</u>:

Não [!DNL JS] erros e as alterações à [!DNL staging] as atualizações do foram salvas com sucesso.

<u>Resultados reais</u>:

[!DNL JS] erros forem visíveis no console, o formulário estiver malformado e a variável [!DNL spinner] nunca é desativado após salvar.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.
