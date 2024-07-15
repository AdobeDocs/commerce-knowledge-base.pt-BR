---
title: "ACSD-48813: a pesquisa não mostra resultados relevantes com base no peso da pesquisa de atributos"
description: Aplique o patch ACSD-48813 para corrigir o problema do Adobe Commerce em que a pesquisa não está mostrando resultados relevantes com base no peso da pesquisa dos atributos.
exl-id: 089e3ab3-0dfa-4f81-85c7-f6060f326d97
feature: Admin Workspace, Attributes, Search
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# ACSD-48813: a pesquisa não mostra resultados relevantes com base no peso da pesquisa de atributos

O patch ACSD-48813 corrige o problema em que a pesquisa não mostra resultados relevantes com base no peso da pesquisa dos atributos. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.29 está instalado. A ID do patch é ACSD-48813. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3 - 2.4.6

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A pesquisa não está mostrando resultados relevantes com base no peso da pesquisa dos atributos.

<u>Etapas a serem reproduzidas</u>:

1. Instale o Adobe Commerce com dados de amostra.
1. Defina o mecanismo de pesquisa como [!DNL Elasticsearch].
1. Faça logon como administrador.
1. Vá para **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Products]**.
1. Abra o atributo *name*.
1. Abra a guia *[!UICONTROL Properties]* da loja.
1. Selecione [!UICONTROL Search Weight] = *10* no valor suspenso.
1. Clique em **[!UICONTROL Save Attribute]**.
1. Agora abra a vitrine e pesquise a palavra *Voltar*.

<u>Resultados esperados</u>:

Os produtos da mochila são retornados na parte superior dos resultados da pesquisa.

<u>Resultados reais</u>:

Os produtos da mochila são retornados no meio dos resultados da pesquisa.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] versão: uma nova ferramenta para autoatender patches de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando o [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
