---
title: '"ACSD-51431: O status do indexador é *[!UICONTROL Working]* mesmo que não haja entradas no changelog'''
description: Aplique o patch ACSD-51431 para corrigir o problema do Adobe Commerce em que o status do indexador é *[!UICONTROL Working]* mesmo se não houver entradas no changelog.
feature: Logs, Price Indexer
role: Admin
exl-id: 85977b78-7f6b-47c7-b33e-16668bdf98fe
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 0%

---

# ACSD-51431: O status do indexador é *[!UICONTROL Working]* mesmo que não haja entradas no changelog

O patch ACSD-51431 corrige o problema de desempenho em que o status do indexador é *[!UICONTROL Working]* mesmo que não haja entradas no changelog. Este patch está disponível quando a variável [!DNL Quality Patches Tool (QPT)] O 1.1.33 está instalado. A ID do patch é ACSD-51431. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.7 - 2.4.6-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O status do indexador é *[!UICONTROL Working]* mesmo que não haja entradas no changelog.

<u>Etapas a serem reproduzidas</u>:

1. Definir **[!UICONTROL indexers]** para [!UICONTROL Update on Schedule].
1. Configure o trabalho cron a ser executado a cada minuto.
1. Salve as alterações em diferentes produtos simultaneamente.
1. Executar `bin/magento indexer:status` em alguns minutos.

<u>Resultados esperados</u>:

As alterações são processadas e os indexadores estão em *[!UICONTROL Ready]* status. A variável *[!UICONTROL Schedule]* o status é *[!UICONTROL idle (0 in the backlog)]*.

<u>Resultados reais</u>:

As alterações são processadas e os indexadores estão em *[!UICONTROL Ready]* status. No entanto, a *[!UICONTROL Schedule]* exibições de status *[!UICONTROL working (0 in the backlog)]*.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.
