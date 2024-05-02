---
title: "ACSD-48212: a importação de produto atribui o produto à origem errada"
description: Aplique o patch ACSD-48212 para corrigir o problema do Adobe Commerce em que a importação de produto atribui o produto à origem errada.
exl-id: b3426f62-f73a-4b76-8e0e-544a9133720f
feature: Admin Workspace, Data Import/Export, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# ACSD-48212: a importação de produto atribui o produto à origem errada

O patch ACSD-48212 corrige o problema em que a importação de produto atribui o produto à origem errada. Este patch está disponível quando a variável [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.26 está instalado. A ID do patch é ACSD-48212. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.7 - 2.4.6

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A importação de produto atribui o produto à origem errada.

<u>Etapas a serem reproduzidas</u>:

1. Crie uma origem de inventário secundária.
1. Crie um produto somente com a origem de estoque padrão.
1. Exporte o produto.
1. Executar `bin/magento cron:run`.
1. Abertura **[!UICONTROL Catalog]** > **[!UICONTROL Prdoucts]**.
1. Selecione o produto na grade.
1. Cancelar atribuição do estoque usando o *[!UICONTROL mass action]* menu.
1. Executar `bin/magento cron:run`.
1. Atribuir a origem secundária usando o *[!UICONTROL mass action]* menu.
1. Executar `bin/magento cron:run`.
1. Exclua o produto usando o *[!UICONTROL mass action]* menu.
1. Executar `bin/magento cron:run`.
1. Importe o produto usando o CSV exportado anteriormente.
1. Verifique a atribuição de origem.

<u>Resultados esperados</u>:

O produto é atribuído somente à origem padrão.

<u>Resultados reais</u>:

O produto é atribuído à origem padrão e secundária.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.
