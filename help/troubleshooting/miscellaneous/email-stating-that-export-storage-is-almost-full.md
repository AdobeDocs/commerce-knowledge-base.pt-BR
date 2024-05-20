---
title: 'Email informando que o armazenamento de exportações está quase cheio'
description: Este artigo fornece uma solução para o problema em que você recebe um e-mail informando que o armazenamento de exportações está quase cheio.
feature: Cloud, Storage, Media
role: Developer
source-git-commit: 8f783cb4245911bded5e9946917e2f2c3e78a705
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 0%

---

# Email informando que o armazenamento de exportações está quase cheio

Este artigo fornece uma solução para o problema em que você recebe um e-mail informando que o armazenamento de exportações está quase cheio.

## Produtos e versões afetados

Adobe Commerce na infraestrutura em nuvem (todas as versões)

## Problema

Você recebe um email com o seguinte conteúdo, mas não consegue localizar o *exportações* pasta:

*Nosso monitoramento detectou que o armazenamento &quot;exportações&quot; no cluster XXX está cerca de &quot;85%&quot; cheio.*
*Se necessário, revise o uso, faça uma limpeza ou solicite um upsize.*
*Além disso, observe que tentaremos um upsize automaticamente quando o armazenamento atingir o nível de limite crítico.*

## Causa

O email se refere ao **exportações** armazenamento, que é a quantidade de disco alocada para os arquivos/mídia, e não uma pasta específica chamada *exportações*.

## Solução

Você deve revisar o uso de arquivos no ambiente. Execute este comando para obter o uso existente:

`df -h |grep data`

Os locais típicos em que o armazenamento de arquivos provavelmente será preenchido são *pub/media/catalog/product/cache* ou *var/log* pastas. Para determinar o espaço em disco usado pelos arquivos, execute este comando com o caminho apropriado */path/to/folder*:

`du -shc` */path/to/folder*

Se o uso do disco de mídia constituir uma grande proporção do espaço total em disco, considere ativar [Otimização profunda de imagens do Fastly](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/fastly-image-optimization#deep-image-optimization)e exclua os arquivos na variável *pub/media/catalog/product/cache* no servidor manualmente.

## Leitura relacionada

[Verificar clusters dedicados](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space#check-dedicated-clusters) em nossa base de conhecimento de suporte.