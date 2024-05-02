---
title: '"Erro do Fastly: A versão do VCL do plug-in está desatualizada! Recarregue'''
description: Este artigo fornece uma solução para quando você visualizar a mensagem "*A versão do VCL do plug-in está desatualizada! Faça upload novamente.*" na Configuração do Fastly, no Administrador do Commerce, devido a não ter instalado o módulo Fastly mais recente.
exl-id: d7870e9e-ba6b-49c2-a80c-26fb464cbae3
feature: Best Practices, Cache
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# Erro do Fastly: a versão do VCL do plug-in está desatualizada! Faça upload novamente

Este artigo fornece uma solução para quando você visualizar a mensagem &quot;*A versão do VCL do plug-in está desatualizada! Faça upload novamente.*&quot; na Configuração do Fastly, no Administrador do Commerce, devido a não ter instalado o módulo Fastly mais recente.

## Produtos e versões afetados

Adobe Commerce na infraestrutura em nuvem 2.2.x., 2.3.x<br>
Fastly: esse erro pode afetar todas as versões do módulo Fastly, exceto a mais recente. Para obter informações sobre a versão mais recente, consulte [Notas de versão do Fastly](https://github.com/fastly/fastly-magento2/releases) no GitHub.

## Problema

1. Faça logon no painel de Administração do Commerce.
1. Navegue até **Lojas** > **Configuração** > **Avançado** > **Sistema** > **Cache de Página Inteira**   **Cache Fastly.**
1. No **Ativação automática de upload e serviço** seção, haverá uma &quot;*A versão do VCL do plug-in está desatualizada! Faça upload novamente.*&quot;.
1. Você tenta fazer upload dos trechos de VCL clicando no botão &quot;Fazer upload do VCL para o Fastly&quot;, mas você ainda vê o aviso &quot;*A versão do VCL do plug-in está desatualizada! Faça upload novamente.*&quot;

## Causa

A extensão do Fastly foi atualizada (junto com uma configuração de VCL agrupada e modelos), mas a configuração de VCL atualizada não foi carregada no serviço Fastly. Ao atualizar o módulo Adobe Commerce `Fastly_Cdn`, carregue uma configuração de VCL atualizada para o Fastly novamente.

## Solução

1. Verifique se as ECE-Tools mais recentes estão instaladas no [versão atual](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/release-notes/cloud-tools-suite.html) na documentação do desenvolvedor. ECE-Tools tem uma versão do pacote Fastly em suas dependências.

   Esta pode não ser a versão mais recente do plug-in Fastly, mas é provável que seja uma versão posterior à que você instalou no momento, e é prática recomendada ter o ECE-Tools mais recente instalado.

1. Se você não estiver na versão atual do ECE-Tools, siga estas etapas para [atualização](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package.html) na documentação do desenvolvedor.
1. Depois de atualizar as ECE-Tools, verifique se você tem uma versão atual da [Plug-in Fastly](https://github.com/fastly/fastly-magento2/tree/master/etc/vcl_snippets) instalado.
1. Se o plug-in Fastly não for a versão atual, siga estas etapas para [atualizar o plug-in para a versão mais recente](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#upgrade-the-fastly-module) na documentação do desenvolvedor.

## Leitura relacionada

* Para obter informações sobre a instalação e configuração do Fastly, consulte [Configurar os serviços do Fastly](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly.html) na documentação do desenvolvedor.
* Para obter informações gerais sobre o Fastly, consulte [fastly.com](https://www.fastly.com/).
