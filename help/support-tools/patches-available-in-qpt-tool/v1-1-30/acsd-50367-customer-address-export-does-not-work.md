---
title: "ACSD-50367: a exportação de endereço do cliente não funciona com o atributo de seleção múltipla"
description: Aplique o patch ACSD-50367 para corrigir o problema do Adobe Commerce em que a exportação de endereço do cliente não funciona quando um atributo de seleção múltipla **`Endereço do cliente`** sem valores é criado.
exl-id: 688831d4-b49e-48fa-b4db-1328cda09a2b
feature: Admin Workspace, Attributes, Data Import/Export, Shipping/Delivery
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# ACSD-50367: a exportação de endereço do cliente não funciona

O patch ACSD-50367 corrige o problema em que a exportação de endereço do cliente não funciona quando uma seleção múltipla **`Customer Address`** atributo sem valores é criado. Este patch está disponível quando a variável [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.30 está instalado. A ID do patch é ACSD-50367. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.7 - 2.4.6

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A exportação de endereço do cliente não funciona quando uma seleção múltipla **`Customer Address`** atributo sem valores é criado.

<u>Pré-requisitos</u>:

Crie um cliente com um endereço.

<u>Etapas a serem reproduzidas</u>:

1. Criar uma seleção múltipla **`Customer Address`** atributo em **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Customer Addresses]**.
1. Ir para **[!UICONTROL Admin]** > **[!UICONTROL System]** > **[!UICONTROL Export]** e selecione **`Customer Address`** tipo de entidade.
1. Exporte os endereços do cliente. Você verá que nada é exportado.
1. Excluir a seleção múltipla **`Customer Address`** e exporte os endereços do cliente novamente. Dessa vez, o arquivo CSV dos endereços é gerado.

<u>Resultados esperados</u>:

Os endereços do cliente podem ser exportados como um arquivo CSV quando uma seleção múltipla **`Customer Address`** atributo é criado.

<u>Resultados reais</u>:

Os endereços do cliente não podem ser exportados como um arquivo CSV quando uma seleção múltipla **`Customer Address`** atributo é criado.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.
