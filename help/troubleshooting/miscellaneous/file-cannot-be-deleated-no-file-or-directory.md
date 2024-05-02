---
title: "O arquivo não pode ser excluído. Aviso! desvincular: esse erro de arquivo ou diretório não existe no [!DNL Admin]"
description: Este artigo fornece uma solução para o problema em que você vê um erro *O arquivo não pode ser excluído. Aviso!desvincular Esse erro de arquivo ou diretório* do [!DNL Admin] quando você faz uma [!DNL Javascript/CSS] liberar.
feature: Admin Workspace, Observability
role: Developer
exl-id: db265e3c-a809-4404-839a-273001e81d22
source-git-commit: fd5fd6e1bc04db56497a2e0c2a96bc1b06d4f7a1
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 0%

---

# *O arquivo não pode ser excluído. Aviso!unlink: erro de arquivo ou diretório inexistente* do [!DNL Admin]

Este artigo fornece uma solução para o problema em que você vê um erro *O arquivo não pode ser excluído. Aviso!unlink: erro de arquivo ou diretório inexistente* do [!DNL Commerce Admin] quando você faz uma [!DNL JavaScript/CSS] liberar.

## Produtos e versões afetados

* Adobe Commerce 2.4.0 - 2.4.6, todos os métodos de implantação

## Problema

Ocorre um erro ao fazer uma [!DNL JS/CSS] liberação:

*O arquivo &quot;/app/pub/static/_cache/merded/.nfsa42d0e64799fd100000001b&quot; não pode ser excluído. Aviso!unlink(/app/pub/static/_cache/merded/.nfsa42d0e64799fd100000001b): esse arquivo ou diretório não existe*

Ou: você vê o erro acima no [!DNL Admin]e/ou um erro semelhante no [!DNL New Relic] ou nos logs de implantação.

Ou: Você não pode acessar os Relatórios avançados e o trabalho analytics_collect_data cron está falhando com este erro:

*O arquivo &quot;/app/var/tmp/analytics/tmp/.nfsb3b6041dd44588a0000850c0&quot; não pode ser excluído. Aviso!unlink(/app/var/tmp/analytics/tmp/.nfsb3b6041dd44588a0000850c0): Arquivo ou diretório inexistente*

<u>Etapas a serem reproduzidas:</u>

Método 1:

1. Faça logon no [!DNL Admin].
1. Ir para **[!UICONTROL System]** > **[!UICONTROL Cache Management]**.
1. Clique em **[!UICONTROL Flush][!DNL JavaScript/CSS][!UICONTROL Cache]**.

Método 2:

1. Faça logon no [!DNL Admin].
1. Ir para **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]**.
1. Faça alterações no [!UICONTROL Base URL] ou [!UICONTROL Base URL (Secure)].
1. Clique em **[!UICONTROL Save Config]**.

## Solução

Se você estiver usando a infraestrutura do Adobe Commerce na nuvem e tiver [!DNL magento/magento-cloud-patches] 1.0.22 instalado que inclui o patch, você não precisa instalar separadamente o ACSD-50165.

Infraestrutura do Adobe Commerce na nuvem: atualize os patches da nuvem do Commerce para a 1.0.22 (**ou mais recente**) que contém esta correção: [Patches da nuvem para o Commerce](/docs/commerce-cloud-service/user-guide/release-notes/cloud-patches.html).

Adobe Commerce no local: aplique o ACSD-50165 usando [Ferramentas de correção de qualidade > Uso](/docs/commerce-operations/tools/quality-patches-tool/usage.html). O patch ACSD-50165 vem com [!DNL QPT] [v1.1.30](/docs/commerce-operations/tools/quality-patches-tool/release-notes.html#v1-1-30)

## Leitura relacionada

* [[!DNL Quality Patches Tool] > Notas de versão](/docs/commerce-operations/tools/quality-patches-tool/release-notes.html) no guia Ferramentas do Commerce.
* [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia Ferramentas do Commerce.
