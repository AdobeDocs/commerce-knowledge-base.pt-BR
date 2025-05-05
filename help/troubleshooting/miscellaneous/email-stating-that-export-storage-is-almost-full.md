---
title: Email informando que o armazenamento de exportações está quase cheio
description: Este artigo fornece uma solução para o problema em que você recebe um e-mail informando que o armazenamento de exportações está quase cheio.
feature: Cloud, Storage, Media
role: Developer
exl-id: 7dae295c-919c-46c5-bf63-7d3467c2e07f
source-git-commit: 89f985b832545f1fbccf94aac1d60f1e767b5bc4
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 0%

---

# Email informando que o armazenamento de exportações está quase cheio

Este artigo fornece uma solução para o problema em que você recebe um e-mail informando que o armazenamento de exportações está quase cheio.

## Produtos e versões afetados

Adobe Commerce na infraestrutura em nuvem (todas as versões)

## Problema

Você recebe um email com o seguinte conteúdo, mas não consegue localizar a pasta *exportações*:

*Nosso monitoramento detectou que o armazenamento &#39;exportações&#39; no cluster XXX está cerca de &#39;85%&#39; cheio.*
*Se necessário, revise o uso, faça uma limpeza ou solicite um upsize.*
*Além disso, observe que tentaremos um upsize automaticamente quando o armazenamento atingir o nível de limite crítico.*

## Causa

O email se refere ao armazenamento **exports**, que é a quantidade de disco alocada aos arquivos/mídia, e não a uma pasta específica chamada *exports*.

## Solução

Você deve revisar o uso de arquivos no ambiente. Execute este comando para obter o uso existente:

`df -h |grep data`

Os locais típicos onde o armazenamento de arquivos provavelmente será preenchido são as pastas *pub/media/catalog/product/cache* ou *var/log*. Para determinar o espaço em disco usado pelos arquivos, execute este comando com o caminho apropriado */caminho/para/pasta*:

`du -shc` */caminho/para/pasta*

Se o uso do disco de mídia constituir uma grande parte do espaço total em disco, considere a habilitação do [Fastly Deep Image Otimization](https://experienceleague.adobe.com/pt-br/docs/commerce-cloud-service/user-guide/cdn/fastly-image-optimization#deep-image-optimization) e, em seguida, exclua os arquivos na pasta *pub/media/catalog/product/cache* do servidor manualmente.

## Leitura relacionada

[Verifique os clusters dedicados](https://experienceleague.adobe.com/pt-br/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space#check-dedicated-clusters) em nossa base de dados de conhecimento de suporte.
