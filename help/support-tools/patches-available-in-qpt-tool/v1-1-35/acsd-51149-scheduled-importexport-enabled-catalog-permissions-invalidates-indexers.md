---
title: '"ACSD-51149: programado [!UICONTROL ImportExport] com ativado [!UICONTROL Catalog Permissions] invalida os indexadores'''
description: Aplique o patch ACSD-51149 para corrigir o problema de desempenho do Adobe Commerce em que o [!UICONTROL ImportExport] com ativado [!UICONTROL Catalog Permissions] invalida indexadores.
feature: Cache, Data Import/Export
role: Admin
exl-id: 3a26f4be-8e52-407d-bb25-2841458f3aa5
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 0%

---

# ACSD-51149: programado [!UICONTROL ImportExport] com ativado [!UICONTROL Catalog Permissions] invalida indexadores

O patch ACSD-51149 corrige o problema em que o evento programado [!UICONTROL ImportExport] com ativado [!UICONTROL Catalog Permissions] invalida indexadores. Este patch está disponível quando a variável [!DNL Quality Patches Tool (QPT)] O 1.1.35 está instalado. A ID do patch é ACSD-51149. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.7 - 2.4.6-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Agendado [!UICONTROL ImportExport] com ativado [!UICONTROL Catalog Permissions] invalida indexadores.

<u>Etapas a serem reproduzidas</u>:

1. Ativar *[!UICONTROL Catalog Permissions]*.
1. Definir todos os indexadores como *[!UICONTROL Update by Schedule]*.
1. Crie um produto simples.
1. Exportar este produto via **[!UICONTROL System]** > **[!UICONTROL Data Transfer]** > **[!UICONTROL Export]**.
1. Baixe o CSV exportado e coloque-o em `<AC root folder>/var/import`.
1. Crie uma importação de produto agendada com o CSV baixado.
1. Executar reindexação completa.
1. Verifique o status dos indexadores. Todos os indexadores devem estar em *[!UICONTROL Ready]* status.
1. Execute a importação agendada criada na grade.
1. Verifique novamente o status dos indexadores.

<u>Resultados esperados</u>:

Todos os indexadores estão no *[!UICONTROL Ready]* status.

<u>Resultados reais</u>:

Alguns indexadores estão em *[!UICONTROL Reindex Required]* status.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.
