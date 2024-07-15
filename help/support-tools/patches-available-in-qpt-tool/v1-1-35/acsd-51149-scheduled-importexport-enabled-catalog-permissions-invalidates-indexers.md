---
title: "ACSD-51149: Agendado [!UICONTROL ImportExport] com [!UICONTROL Catalog Permissions] habilitado invalida indexadores"
description: Aplique o patch ACSD-51149 para corrigir o problema de desempenho do Adobe Commerce em que o [!UICONTROL ImportExport] agendado com [!UICONTROL Catalog Permissions] habilitado invalida os indexadores.
feature: Cache, Data Import/Export
role: Admin
exl-id: 3a26f4be-8e52-407d-bb25-2841458f3aa5
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 0%

---

# ACSD-51149: Agendado [!UICONTROL ImportExport] com [!UICONTROL Catalog Permissions] habilitado invalida indexadores

O patch ACSD-51149 corrige o problema em que o [!UICONTROL ImportExport] agendado com [!UICONTROL Catalog Permissions] habilitado invalida os indexadores. Este patch está disponível quando o [!DNL Quality Patches Tool (QPT)] 1.1.35 está instalado. A ID do patch é ACSD-51149. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.7 - 2.4.6-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O agendamento de [!UICONTROL ImportExport] com [!UICONTROL Catalog Permissions] habilitado invalida os indexadores.

<u>Etapas a serem reproduzidas</u>:

1. Habilitar *[!UICONTROL Catalog Permissions]*.
1. Definir todos os indexadores como *[!UICONTROL Update by Schedule]*.
1. Crie um produto simples.
1. Exportar este produto via **[!UICONTROL System]** > **[!UICONTROL Data Transfer]** > **[!UICONTROL Export]**.
1. Baixe o CSV exportado e coloque-o em `<AC root folder>/var/import`.
1. Crie uma importação de produto agendada com o CSV baixado.
1. Executar reindexação completa.
1. Verifique o status dos indexadores. Todos os indexadores devem estar no status *[!UICONTROL Ready]*.
1. Execute a importação agendada criada na grade.
1. Verifique novamente o status dos indexadores.

<u>Resultados esperados</u>:

Todos os indexadores estão no status *[!UICONTROL Ready]*.

<u>Resultados reais</u>:

Alguns dos indexadores estão com o status *[!UICONTROL Reindex Required]*.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] versão: uma nova ferramenta para autoatender patches de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando o [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
