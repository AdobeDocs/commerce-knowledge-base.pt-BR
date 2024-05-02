---
title: "ACSD-48661: problema de validação do separador de vírgula do limite de crédito da empresa"
description: Aplique o patch ACSD-48661 para corrigir o problema do Adobe Commerce em que, quando o limite de crédito da empresa é maior que 999, o separador de vírgulas impede o salvamento da empresa devido a um erro de validação.
exl-id: 85c5a93f-76c5-439b-adcc-511f8473f302
feature: Admin Workspace, B2B, Companies, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '417'
ht-degree: 0%

---

# ACSD-48661: problema de validação do separador de vírgula do limite de crédito da empresa

O patch ACSD-48661 corrige o problema em que, quando o limite de crédito da empresa é maior que 999, o separador de vírgulas impede o salvamento da empresa devido a um erro de validação. Este patch está disponível quando a variável [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.26 está instalado. A ID do patch é ACSD-48661. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.7 - 2.4.5-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Quando o limite de crédito da empresa é maior que 999, o separador de vírgulas impede que a empresa seja salva devido a um erro de validação.

<u>Etapas a serem reproduzidas</u>:

1. Habilitar o recurso da empresa em **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]**.
1. Crie uma empresa e adicione um limite de crédito maior que 999 sob o **[!UICONTROL Company Credit]** guia.
1. Salve a empresa.
1. Edite a empresa e tente salvá-la novamente.

<u>Resultados esperados</u>:

Você pode salvar a empresa sem fixar o limite de crédito. A vírgula não é compatível com campos de entrada para valores e preços.

<u>Resultados reais</u>:

Não é possível salvar a empresa devido a um erro de validação na *[!UICONTROL Credit Limit]* campo. O Adobe Commerce adiciona separadores de vírgula automaticamente para limites de crédito, mesmo que a variável [!UICONTROL Credit Limit] O campo não aceita vírgulas.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.
