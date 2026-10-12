---
title: Imagens de armazenamento não exibidas após a implantação
description: Este artigo fornece uma solução para quando as imagens não estiverem sendo exibidas corretamente após a implantação.
exl-id: 7e6bcebd-edff-437a-9103-2743443d2ed9
feature: Cache, Categories, Deploy, Storefront
role: Admin
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: bcd8874c-7b93-5596-bdaa-22660e84df14
    internal-label: Deploy
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
    internal-label: Storefront
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
  - id: e91a50b1-0b31-436e-9033-00e4776e94cb
    internal-label: Categories
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '184'
ht-degree: 0%
---
# Imagens de armazenamento não exibidas após a implantação

Este artigo fornece uma solução para quando as imagens não estiverem sendo exibidas corretamente após a implantação.

## Produtos e versões afetados

* Adobe Commerce na infraestrutura em nuvem 2.2.x, 2.3.x

## Problema

Quando você usa um tema de vitrine com redimensionamento de imagem, as imagens não são exibidas ou desaparecem das páginas do catálogo quando implantadas.

## Causa

Isso pode ocorrer devido ao carregamento das imagens do cache.

## Solução

Se isso acontecer, você poderá usar o comando Magento para gerar novamente o cache da imagem e exibir as imagens corretamente.

Para fazer isso, você precisa das informações de SSH e da URL de armazenamento disponível por meio do [Cloud Console](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html).

1. SSH para o seu projeto que era uma origem para o [despejo de banco de dados](/help/how-to/general/create-database-dump-on-cloud.md), conforme descrito em [SSH para o ambiente](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/secure-connections) na documentação do desenvolvedor.
1. Gere novamente o cache de imagens executando:

   ```bash
   php bin/magento catalog:images:resize
   ```

1. Teste as páginas de categoria por meio do URL de armazenamento.
