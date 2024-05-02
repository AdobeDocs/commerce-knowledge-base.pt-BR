---
title: "ACSD-52143: as opções personalizadas são removidas após a importação do produto"
description: Aplique o patch ACSD-52143 para corrigir o problema do Adobe Commerce em que as opções de personalização são removidas após a importação do produto.
feature: Data Import/Export
role: Admin, Developer
exl-id: 7dde1efe-37a3-443f-9ce1-82cf1b3d9da7
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# ACSD-52143: as opções personalizadas são removidas após a importação do produto

O patch ACSD-52143 corrige o problema em que as opções personalizadas são removidas após a importação do produto. Este patch está disponível quando a variável [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.37 está instalado. A ID do patch é ACSD-52143. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6 - 2.4.6-p2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

As opções personalizadas são removidas após a importação do produto.

<u>Etapas a serem reproduzidas</u>:

1. Ir para **[!UICONTROL Store]** > **[!UICONTROL All Stores]** e configurar uma instância de várias lojas (um site com duas visualizações de loja).
1. Ir para **[!UICONTROL Catalog]** > **[!UICONTROL Products]** e criar dois produtos com [!UICONTROL Customizable Options].
1. Em cada produto, adicione um [!UICONTROL Customizable Option].
1. Alterne para a segunda exibição de loja e modifique o nome do produto em cada produto.
1. Ir para **[!UICONTROL System]** > **[!UICONTROL Data Transfer]** > **[!UICONTROL Export]** e exporte os dois produtos criados.
1. Baixe o arquivo CSV.
1. Ir para **[!UICONTROL System]** > **[!UICONTROL Data Transfer]** > **[!UICONTROL Import]** e reimporte o arquivo.
1. Verifique os dois produtos.

<u>Resultados esperados</u>:

As opções personalizadas não são removidas após a importação do produto.

<u>Resultados reais</u>:

As opções de imposto alfandegário são removidas após a importação do produto.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.
