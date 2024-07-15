---
title: "Correção de Magento MDVA-23426: emails enviados como anexos do Outlook"
description: O patch de Magento MDVA-23426 corrige o problema em que os emails são enviados como anexos por Magento do MS Outlook. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.13 está instalada. Observe que o problema foi corrigido na Magento 2.3.5.
exl-id: 0b4c3e33-76c5-48b0-b1a8-a967cea11b98
feature: Communications
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 0%

---

# Correção de Magento MDVA-23426: emails enviados como anexos do Outlook

O patch de Magento MDVA-23426 corrige o problema em que os emails são enviados como anexos por Magento do MS Outlook. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.13 está instalada. Observe que o problema foi corrigido na Magento 2.3.5.

## Produtos e versões afetados

**O patch foi criado para a versão do Magento:** Magento Commerce Cloud 2.3.3.

**Compatível com as versões de Magento:** Magento Commerce e Magento Commerce Cloud 2.3.3 - 2.3.4-p2.

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os emails são recebidos com um corpo em branco e o conteúdo é incluído como um anexo.

<u>Pré-requisitos:</u> o Outlook/Exchange está sendo usado como a combinação cliente/servidor.

<u>Etapas a serem reproduzidas:</u> 1. Enviar um pedido, a notificação do pedido ou a notificação da entrega.2. O email é recebido.

<u>Resultado real:</u> o email é exibido com um corpo em branco e o conteúdo é incluído como um anexo com rótulo ATT\* ao email. <u>Resultado esperado:</u>

O email é recebido sem anexo e o corpo do email contém o conteúdo.

## Aplicar o patch

Para obter instruções sobre como aplicar um patch QPT, use os seguintes links, dependendo do seu produto Magento:

* Magento Commerce: DevDocs [Aplique patches usando a Ferramenta de Patches de Qualidade](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) .
* Magento Commerce Cloud: DevDocs [Atualizações e Patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) .

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender patches de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [Verifique o problema de Magento com a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) .

Para obter informações sobre outros patches disponíveis na ferramenta QPT, consulte a seção [Patches disponíveis na ferramenta QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).
