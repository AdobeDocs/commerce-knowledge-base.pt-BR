---
title: Imagens de armazenamento não exibidas após a implantação
description: Este artigo fornece uma solução para quando as imagens não estiverem sendo exibidas corretamente após a implantação.
exl-id: 7e6bcebd-edff-437a-9103-2743443d2ed9
feature: Cache, Categories, Deploy, Storefront
role: Admin
source-git-commit: c4d586ca3980acbe4f33c5f2616ef7f3051bc7d3
workflow-type: tm+mt
source-wordcount: '162'
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

Se isso acontecer, você poderá usar o comando Magento para gerar novamente o cache de imagens e exibi-las corretamente.

Para fazer isso, você precisa das informações SSH e do URL de armazenamento disponível por meio do [Cloud Console](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html).

1. SSH para o seu projeto que era uma fonte para a variável [dump do banco de dados](/help/how-to/general/create-database-dump-on-cloud.md), conforme descrito em [SSH para o ambiente](https://devdocs.magento.com/guides/v2.3/cloud/env/environments-ssh.html#ssh) na documentação do desenvolvedor.
1. Gere novamente o cache de imagens executando:

   ```bash
   php bin/magento catalog:images:resize
   ```

1. Teste as páginas de categoria por meio do URL de armazenamento.
