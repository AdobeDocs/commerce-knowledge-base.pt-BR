---
title: 'ACSD-51431: O status do indexador é *[!UICONTROL Working]* mesmo se não houver entradas no changelog'
description: Aplique o patch ACSD-51431 para corrigir o problema do Adobe Commerce em que o status do indexador é *[!UICONTROL Working]* mesmo que não haja entradas no changelog.
feature: Logs, Price Indexer
role: Admin
exl-id: 85977b78-7f6b-47c7-b33e-16668bdf98fe
source-git-commit: 8b6bf1cdada7edb0cdb0bb3e90ed15ee8cebf77e
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 0%

---

# ACSD-51431: O status do indexador é *[!UICONTROL Working]* mesmo se não houver entradas no changelog

O patch ACSD-51431 corrige o problema de desempenho em que o status do indexador é *[!UICONTROL Working]* mesmo que não haja entradas no changelog. Este patch está disponível quando o [!DNL Quality Patches Tool (QPT)] 1.1.33 está instalado. A ID do patch é ACSD-51431. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.7 - 2.4.6-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O status do indexador é *[!UICONTROL Working]* mesmo sem entradas no changelog.

<u>Etapas a serem reproduzidas</u>:

1. Defina **[!UICONTROL indexers]** como [!UICONTROL Update on Schedule].
1. Configure o trabalho cron a ser executado a cada minuto.
1. Salve as alterações em diferentes produtos simultaneamente.
1. Execute `bin/magento indexer:status` em alguns minutos.

<u>Resultados esperados</u>:

As alterações são processadas e os indexadores estão no status *[!UICONTROL Ready]*. O status de *[!UICONTROL Schedule]* é *[!UICONTROL idle (0 in the backlog)]*.

<u>Resultados reais</u>:

As alterações são processadas e os indexadores estão no status *[!UICONTROL Ready]*. No entanto, o status de *[!UICONTROL Schedule]* exibe *[!UICONTROL working (0 in the backlog)]*.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] versão: uma nova ferramenta para autoatender patches de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando o [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
