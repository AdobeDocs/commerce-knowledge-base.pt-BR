---
title: Atualizações programadas do armazenamento temporário de conteúdo não são exibidas com o cache obsoleto do Fastly
description: Este artigo fornece uma correção para quando as lojas Adobe Commerce não exibem atualizações programadas ao usar o armazenamento temporário de conteúdo e o Fastly. O problema se deve ao Fastly Soft Purge habilitado por padrão. Esse recurso reduz a carga de recursos do aplicativo e apenas regenera um cache novo em uma segunda solicitação. Para resolver isso, você pode ativar a página Limpar CMS por meio do Administrador do Commerce para sempre regenerar e fornecer conteúdo novo.
exl-id: becbffaa-b6dd-4e9b-894e-17901c40223a
feature: CMS, Cache, Page Content, Staging
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: ddbd0f6e-b569-5a04-8a70-55058777c373
    internal-label: CMS
  - id: 17d326fa-534a-55a5-b46f-8ae1de1e2f75
    internal-label: Page Content
  - id: 0054e3a7-7067-583b-bfd2-ab39dada9ab5
    internal-label: Staging
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '491'
ht-degree: 0%
---
# Atualizações programadas do armazenamento temporário de conteúdo não são exibidas com o cache obsoleto do Fastly

Este artigo fornece uma correção para quando as lojas Adobe Commerce não exibem atualizações programadas ao usar o armazenamento temporário de conteúdo e o Fastly. O problema se deve ao Fastly Soft Purge habilitado por padrão. Esse recurso reduz a carga de recursos do aplicativo e apenas regenera um cache novo em uma segunda solicitação. Para resolver isso, você pode ativar a página Limpar CMS por meio do Administrador do Commerce para sempre regenerar e fornecer conteúdo novo.

## Problema

Atualizações programadas para um ativo de conteúdo de armazenamento (página, produto, bloco etc.) não são exibidos na loja imediatamente após a hora de início da atualização. Isso acontece quando as atualizações foram agendadas usando a funcionalidade [Preparo de conteúdo](https://experienceleague.adobe.com/docs/commerce-admin/content-design/staging/content-staging.html).

## Causa

Devido à funcionalidade de Limpeza suave do Fastly (habilitada por padrão), a loja do Adobe Commerce ainda recebe o conteúdo antigo em cache (obsoleto) ao enviar a **primeira** solicitação do ativo atualizado para o Fastly. O Fastly requer uma segunda solicitação para gerar novamente os dados do site.

Como resultado, o Fastly pode enviar conteúdo obsoleto até a segunda solicitação do conteúdo atualizado.

**Cache esperado:** depois que agendamos uma atualização para um ativo de conteúdo usando o Armazenamento temporário de conteúdo, o Adobe Commerce envia uma solicitação para atualizar o cache para o Fastly. O Fastly invalida o conteúdo em cache anterior (sem excluir o conteúdo) e inicia o fornecimento do conteúdo atualizado.

**Cache real:** se o Fastly ainda enviar o conteúdo obsoleto ao receber a **primeira** solicitação do conteúdo atualizado, ele só enviará conteúdo regenerado e correto depois de receber a **segunda** solicitação. Esse comportamento foi implementado para reduzir a carga do servidor, renovando o cache somente em áreas com tráfego comprovado, sem regenerar o cache para todo o site. O Fastly atualiza o cache gradualmente, salvando os recursos do aplicativo.

## Solução

Se veicular conteúdo obsoleto mesmo para a primeira solicitação for inaceitável, você poderá desativar a Expurgação reversível e ativar a página Expurgar CMS:

1. Faça logon no Administrador local do Commerce como administrador.
1. Vá para **Lojas** > **Configuração** > **Avançado** > **Sistema** > **Cache de Página Inteira**.
1. Expanda **Configuração Rápida** e **Avançado**.
1. Definir **Usar Limpeza Flexível** para *Não*.
1. Defina **Limpar página do CMS** como *Sim*.
1. Clique em **Salvar configuração** na parte superior da página.


![purge_options.png](assets/purge_options.png)

## Documentação relacionada

* [Configure as opções de limpeza](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html) no Guia de Infraestrutura do Commerce na Nuvem.
* [Preparo de conteúdo](https://experienceleague.adobe.com/docs/commerce-admin/content-design/staging/content-staging.html) na documentação de Conteúdo e Design.
* [Veiculação de conteúdo obsoleto](https://docs.fastly.com/guides/performance-tuning/serving-stale-content) na documentação do Fastly.
