---
title: Desative a saída do banner do Adobe Commerce para melhorar o desempenho do site
description: Este artigo fornece uma correção para o baixo desempenho do site. O baixo desempenho do site pode ser causado pelo módulo "Magento_Banner" estar ativado, mas não ser usado. Desativar a saída do módulo pode melhorar o desempenho do site. Consulte o artigo para ver as etapas de resolução.
exl-id: 90a8bd21-1f2c-4cfe-8213-17f877e20de8
feature: Configuration
role: Developer
source-git-commit: 76ef59dc37504f50d55734a90c9ce5b30bb83175
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 0%

---

# Desative a saída do banner do Adobe Commerce para melhorar o desempenho do site

Este artigo fornece uma correção para o baixo desempenho do site. O baixo desempenho do site pode ser causado pelo módulo `Magento_Banner` estar habilitado, mas não ser usado. Desativar a saída do módulo pode melhorar o desempenho do site. Consulte o artigo para ver as etapas de resolução.

>[!NOTE]
>
>Se você usa a funcionalidade de banner do Adobe Commerce, consulte o artigo [Solicitações de AJAX de alta taxa de transferência causam baixo desempenho](/help/troubleshooting/miscellaneous/high-throughput-ajax-requests-cause-poor-performance.md) em nossa base de conhecimento de suporte para obter recomendações sobre como evitar problemas de desempenho causados por solicitações excessivas de Ajax.

## Produtos e versões afetados

* Adobe Commerce na infraestrutura em nuvem v.2.x.x
* Adobe Commerce no local v.2.2.x e 2.3.x

## Problema

O módulo `Magento_Banner` está habilitado, mas não está em uso.

Para verificar se esse é o caso:

Para o Adobe Commerce na infraestrutura em nuvem 2.2.x:

1. Faça logon no Administrador do Commerce.
1. Navegue até **[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Banners]**.
1. Se a grade exibida nessa página estiver vazia, significa que você não tem banners.

Se você não vir a opção **[!UICONTROL Banners]** em **[!UICONTROL Content]** > **[!UICONTROL Elements]**, significa que você já aplicou as recomendações deste artigo.

Para o Adobe Commerce na infraestrutura de nuvem 2.3.x e mais recente (a funcionalidade foi [renomeada na v 2.3.x](https://commerce-docs.github.io/devdocs-archive/2.3/guides/v2.3/release-notes/ReleaseNotes2.3.0Commerce.html#banner-now-dynamic-block)):

1. Faça logon no Administrador do Commerce.
1. Navegue até **[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Dynamic Blocks]**.
1. Se a grade exibida nessa página estiver vazia, significa que você não tem blocos dinâmicos (banners).

Se você não vir a opção **[!UICONTROL Dynamic Blocks]** em **[!UICONTROL Content]** > **[!UICONTROL Elements]**, significa que você já aplicou a recomendação deste artigo. Para ver a opção de banners novamente, inverta o processo.

## Causa

Quando o módulo `Magento_Banner` está habilitado, o Adobe Commerce envia solicitações do Ajax da loja para o servidor para obter as informações do banner. Essas solicitações do Ajax têm um impacto no desempenho, especialmente em condições de alta carga (alto volume e alto tráfego). Se a funcionalidade não for usada, é recomendável desativar a saída do módulo. Não é recomendável desativar o módulo, devido a problemas de dependência.

## Solução

>[!WARNING]
>
>Recomendamos testar as alterações em [Ambiente de preparo/integração](/help/announcements/adobe-commerce-announcements/integration-environment-enhancement-request-pro-and-starter.md) primeiro, antes de aplicá-lo à produção. Também recomendamos ter um backup recente antes de qualquer manipulação.

1. Desative a saída do módulo `Magento_Banner`, conforme descrito em [Desativar saída do módulo](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/configuration-guide/files/disable-module-output) na documentação do desenvolvedor. O nome do módulo que você precisa usar é `Magento_Banner`.
1. Implante seu código. Para o Adobe Commerce na infraestrutura em nuvem, implante conforme descrito no artigo [Implante sua loja](https://experienceleague.adobe.com/pt-br/docs/commerce-cloud-service/user-guide/develop/deploy/staging-production) na documentação do desenvolvedor.
1. Depois de desabilitar a saída do módulo, o menu não aparece mais no admin.
1. Você não verá mais a opção Banner ou Dynamic em **[!UICONTROL Content]** > **[!UICONTROL Elements]**. Para mostrar as opções novamente, [habilite a saída do módulo](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/configuration-guide/files/disable-module-output?lang=en#disable-module-output-in-a-simple-deployment).

