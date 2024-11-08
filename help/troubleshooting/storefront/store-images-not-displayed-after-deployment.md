---
title: Imagens de armazenamento não exibidas após a implantação
description: Este artigo fornece uma solução para quando as imagens não estiverem sendo exibidas corretamente após a implantação.
exl-id: 7e6bcebd-edff-437a-9103-2743443d2ed9
feature: Cache, Categories, Deploy, Storefront
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
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

Para fazer isso, você precisa das informações de SSH e da URL de armazenamento disponível por meio do [Cloud Console](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html).

1. SSH para o seu projeto que era uma origem para o [despejo de banco de dados](/help/how-to/general/create-database-dump-on-cloud.md), conforme descrito em [SSH para o ambiente](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/secure-connections) na documentação do desenvolvedor.
1. Gere novamente o cache de imagens executando:

   ```bash
   php bin/magento catalog:images:resize
   ```

1. Teste as páginas de categoria por meio do URL de armazenamento.
