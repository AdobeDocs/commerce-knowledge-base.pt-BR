---
title: '"ACSD-49835: [!UICONTROL Use Default Value] caixa de seleção não foi salva'''
description: Aplique o patch ACSD-49835 para corrigir o problema do Adobe Commerce em que o [!UICONTROL Use Default Value] a caixa de seleção não é salva corretamente no nível do armazenamento para um atributo de seleção múltipla.
exl-id: 84270551-c8a9-4b08-a055-ffdcc538c33d
feature: Storefront
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%

---

# ACSD-49835: [!UICONTROL Use Default Value] a caixa de seleção não está salva

O patch ACSD-49835 corrige o problema em que a variável [!UICONTROL Use Default Value] a caixa de seleção não é salva corretamente no nível do armazenamento para um atributo de seleção múltipla. Este patch está disponível quando a variável [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.29 está instalado. A ID do patch é ACSD-49835. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5 - 2.4.6

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A variável [!UICONTROL Use Default Value] a caixa de seleção não é salva corretamente no nível do armazenamento para um atributo de seleção múltipla.

<u>Etapas a serem reproduzidas</u>:

1. Criar um **[!UICONTROL Multiple-select Attribute]** in **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]** e adicioná-lo a um conjunto de atributos.
1. Vá para uma **[!UICONTROL Product]** e salve **[!UICONTROL Values]** in **[!UICONTROL All Store Views (Default Scope)]**.
1. Ir para um **[!UICONTROL Store View Scope]** e salve o produto.
1. Ir para **[!UICONTROL Store View Scope]** e verifique a **[!UICONTROL Use Default Value]** caixa de seleção

<u>Resultados esperados</u>:

Os valores de atributo de seleção múltipla são salvos corretamente ao verificar a [!UICONTROL Use Default Value] caixa de seleção na caixa [!UICONTROL Store View Scope].

<u>Resultados reais</u>:

Os valores de atributo de seleção múltipla não são salvos corretamente ao verificar a [!UICONTROL Use Default Value] caixa de seleção na caixa [!UICONTROL Store View Scope].

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.
