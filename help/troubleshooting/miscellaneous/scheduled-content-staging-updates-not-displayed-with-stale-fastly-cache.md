---
title: Atualizações programadas do armazenamento temporário de conteúdo não são exibidas com o cache obsoleto do Fastly
description: Este artigo fornece uma correção para quando as lojas Adobe Commerce não exibem atualizações programadas ao usar o armazenamento temporário de conteúdo e o Fastly. O problema se deve ao Fastly Soft Purge habilitado por padrão. Esse recurso reduz a carga de recursos do aplicativo e apenas regenera um cache novo em uma segunda solicitação. Para resolver, você pode ativar a página Limpar CMS por meio do Administrador do Commerce para sempre regenerar e fornecer conteúdo novo.
exl-id: becbffaa-b6dd-4e9b-894e-17901c40223a
feature: CMS, Cache, Page Content, Staging
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 0%

---

# Atualizações programadas do armazenamento temporário de conteúdo não são exibidas com o cache obsoleto do Fastly

Este artigo fornece uma correção para quando as lojas Adobe Commerce não exibem atualizações programadas ao usar o armazenamento temporário de conteúdo e o Fastly. O problema se deve ao Fastly Soft Purge habilitado por padrão. Esse recurso reduz a carga de recursos do aplicativo e apenas regenera um cache novo em uma segunda solicitação. Para resolver, você pode ativar a página Limpar CMS por meio do Administrador do Commerce para sempre regenerar e fornecer conteúdo novo.

## Problema

Atualizações programadas para um ativo de conteúdo de armazenamento (página, produto, bloco etc.) não são exibidos na loja imediatamente após a hora de início da atualização. Isso acontece quando as atualizações foram agendadas usando o [Preparo de conteúdo](https://experienceleague.adobe.com/docs/commerce-admin/content-design/staging/content-staging.html) funcionalidade.

## Causa

Devido à funcionalidade Soft Purge do Fastly (ativada por padrão), a loja do Adobe Commerce ainda recebe o conteúdo antigo (obsoleto) em cache ao enviar **o primeiro** solicitação de atualização do ativo para o Fastly. O Fastly requer uma segunda solicitação para gerar novamente os dados do site.

Como resultado, o Fastly pode enviar conteúdo obsoleto até a segunda solicitação do conteúdo atualizado.

**Armazenamento em cache esperado:** Depois de agendar uma atualização para um ativo de conteúdo usando o Preparo de conteúdo, o Adobe Commerce envia uma solicitação para atualizar o cache para o Fastly. O Fastly invalida o conteúdo em cache anterior (sem excluir o conteúdo) e inicia o fornecimento do conteúdo atualizado.

**Armazenamento em cache real:** Se o Fastly ainda enviar o conteúdo obsoleto ao receber **o primeiro** solicitação para o conteúdo atualizado, ele só enviará conteúdo gerado novamente e correto depois de receber **o segundo** solicitação. Esse comportamento foi implementado para reduzir a carga do servidor, renovando o cache somente em áreas com tráfego comprovado, sem regenerar o cache para todo o site. O Fastly atualiza o cache gradualmente, salvando os recursos do aplicativo.

## Solução

Se o fornecimento de conteúdo obsoleto, mesmo para a primeira solicitação, for inaceitável, você poderá desativar a Expurgação Temporária e ativar a página Expurgar CMS:

1. Faça logon no Administrador local do Commerce como administrador.
1. Ir para **Lojas** > **Configuração** > **Avançado** > **Sistema** > **Cache de Página Inteira**.
1. Expandir **Configuração do Fastly**, em seguida, expandir **Avançado**.
1. Definir **Usar limpeza suave** para *Não*.
1. Definir **Página Expurgar CMS** para *Sim*.
1. Clique em **Salvar configuração** na parte superior da página.


![purge_options.png](assets/purge_options.png)

## Documentação relacionada

* [Configurar opções de limpeza](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html) no Guia de infraestrutura do Commerce na nuvem.
* [Preparo de conteúdo](https://experienceleague.adobe.com/docs/commerce-admin/content-design/staging/content-staging.html) na documentação Conteúdo e design.
* [Disponibilização de conteúdo obsoleto](https://docs.fastly.com/guides/performance-tuning/serving-stale-content) na documentação do Fastly.
