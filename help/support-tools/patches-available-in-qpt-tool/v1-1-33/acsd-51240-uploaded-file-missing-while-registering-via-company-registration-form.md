---
title: "ACSD-51240: arquivo carregado ausente durante o registro por meio do formulário de registro da empresa"
description: Aplique o patch ACSD-51240 para corrigir o problema do Adobe Commerce em que o arquivo carregado está ausente durante o registro por meio do formulário de registro da empresa.
exl-id: e5822c54-4e77-46b0-84b6-5e25c3845974
source-git-commit: e1fe8936c56f422ae591c6424d8a72621093db81
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---

# ACSD-51240: arquivo carregado ausente durante o registro por meio do formulário de registro da empresa

>[!NOTE]
>
>Este patch foi substituído por [ACSD-55628](/help/support-tools/patches-available-in-qpt-tool/v1-1-42/acsd-55628-upload-file-company-registration-form-replace-file-customer-attribute-storefront.md).

O patch ACSD-51240 corrige o problema em que o arquivo carregado está ausente durante o registro por meio do formulário de registro da empresa. Este patch está disponível quando a variável [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.33 está instalado. A ID do patch é ACSD-51240. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 &lt; 2.4.6-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>). Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Problema

O arquivo carregado está ausente durante o registro por meio do formulário de registro da empresa.

<u>Etapas a serem reproduzidas</u>:

1. Definir **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B >Company]** > **[!UICONTROL Enable]** = *Sim*.
1. Criar um novo atributo do cliente de **[!UICONTROL File]** type, set **[!UICONTROL Show in StoreFront]** = *Sim* e selecione **[!UICONTROL all forms]**.
1. Crie uma nova empresa na Loja e faça upload de uma imagem para o novo atributo.
Abra a empresa e o usuário administrador na Loja.

<u>Resultados esperados</u>:

O arquivo carregado é exibido.

<u>Resultados reais</u>:

O arquivo carregado não é exibido na página da empresa nem na página do cliente administrador no [!UICONTROL Commerce Admin].

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.
