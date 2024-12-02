---
title: 'O arquivo não pode ser excluído. Aviso! desvincular: o erro de arquivo ou diretório não existe em  [!DNL Admin]'
description: Este artigo fornece uma solução para o problema em que você vê um erro *O arquivo não pode ser excluído. Aviso!desvincular Esse erro de arquivo ou diretório* do  [!DNL Admin] ao fazer uma [!DNL Javascript/CSS] liberação.
feature: Admin Workspace, Observability
role: Developer
exl-id: db265e3c-a809-4404-839a-273001e81d22
source-git-commit: 8b6bf1cdada7edb0cdb0bb3e90ed15ee8cebf77e
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 0%

---

# *Não é possível excluir o arquivo. Aviso!unlink: erro de arquivo ou diretório* ausente de [!DNL Admin]

Este artigo fornece uma solução para o problema em que você vê um erro *O arquivo não pode ser excluído. Aviso!unlink: erro de arquivo ou diretório* ausente de [!DNL Commerce Admin] ao fazer uma liberação de [!DNL JavaScript/CSS].

## Produtos e versões afetados

* Adobe Commerce 2.4.0 - 2.4.6, todos os métodos de implantação

## Problema

Ocorre um erro ao fazer uma liberação do [!DNL JS/CSS]:

*O arquivo &quot;/app/pub/static/_cache/merded/.nfsa42d0e64799fd100000001b&quot; não pode ser excluído. Aviso!unlink(/app/pub/static/_cache/merded/.nfsa42d0e64799fd100000001b): Arquivo ou diretório inexistente*

Ou: Você vê o erro acima no [!DNL Admin] e/ou um erro semelhante no [!DNL New Relic] ou nos logs de implantação.

Ou: Você não pode acessar os Relatórios avançados e o trabalho analytics_collect_data cron está falhando com este erro:

*O arquivo &quot;/app/var/tmp/analytics/tmp/.nfsb3b6041dd44588a0000850c0&quot; não pode ser excluído. Aviso!unlink(/app/var/tmp/analytics/tmp/.nfsb3b6041dd44588a0000850c0): Arquivo ou diretório inexistente*

<u>Etapas a serem reproduzidas:</u>

Método 1:

1. Faça logon no [!DNL Admin].
1. Vá para **[!UICONTROL System]** > **[!UICONTROL Cache Management]**.
1. Clique em **[!UICONTROL Flush][!DNL JavaScript/CSS][!UICONTROL Cache]**.

Método 2:

1. Faça logon no [!DNL Admin].
1. Vá para **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]**.
1. Faça alterações no [!UICONTROL Base URL] ou [!UICONTROL Base URL (Secure)].
1. Clique em **[!UICONTROL Save Config]**.

## Solução

Se você estiver na infraestrutura do Adobe Commerce na nuvem e tiver o [!DNL magento/magento-cloud-patches] 1.0.22 instalado, que inclui o patch, não será necessário instalar o ACSD-50165 separadamente.

Infraestrutura do Adobe Commerce na Nuvem: Atualize os Patches da Nuvem do Commerce para a versão 1.0.22 (**ou mais recente**) que contém esta correção: [Patches da Nuvem do Commerce](/docs/commerce-cloud-service/user-guide/release-notes/cloud-patches.html).

Adobe Commerce no local: aplique ACSD-50165 usando [Ferramentas de correção de qualidade > Uso](/docs/commerce-operations/tools/quality-patches-tool/usage.html). O patch ACSD-50165 vem com [!DNL QPT] [v1.1.30.](/docs/commerce-operations/tools/quality-patches-tool/release-notes.html#v1-1-30)

## Leitura relacionada

* [[!DNL Quality Patches Tool] > Notas de versão](/docs/commerce-operations/tools/quality-patches-tool/release-notes.html) no guia Ferramentas do Commerce.
* [[!DNL Quality Patches Tool]: Pesquise por patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia de Ferramentas do Commerce.
