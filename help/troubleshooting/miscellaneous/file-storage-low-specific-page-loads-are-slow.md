---
title: O armazenamento de arquivos é baixo, cargas de página específicas são lentas
description: Este artigo fornece uma solução para o problema de pouco espaço em disco causado por imagens grandes e ricas.
exl-id: 640c8f0d-f714-4cc1-a401-9264cfaf8e37
feature: Storage, Observability
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 0%

---

# O armazenamento de arquivos é baixo, cargas de página específicas são lentas

Este artigo fornece uma solução para o problema de pouco espaço em disco causado por imagens grandes e ricas.

## Produtos e versões afetados

* Adobe Commerce na infraestrutura em nuvem, todas as versões compatíveis
* Adobe Commerce no local, todas as versões com suporte
* Magento Open Source, todas as versões compatíveis

## Problema

O baixo armazenamento em disco e os carregamentos de página lentos podem ser causados por imagens grandes e ricas que usam grandes quantidades de armazenamento no `pub/media/catalog/products` e pelo compartilhamento de espaço em disco entre preparo e produção, (a menos que um ambiente de preparo dedicado seja provisionado).

## Causa

As imagens não são otimizadas para equilibrar o desempenho com a qualidade de visualização.

## Solução

Antes de carregar imagens, otimize-as e compacte-as para equilibrar o desempenho com a qualidade de visualização. Isso ajuda a aumentar o espaço e reduzir o tempo de carregamento da página. PNGs fornecem tamanhos menores para imagens com grandes áreas de cor sólida. JPEG dão tamanhos menores para todo o resto. Use a compactação mais alta (sem degradação visível). Isso geralmente é de 60-80%.

Use a [Rápida otimização de imagens](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly-image-optimization.html) para produzir imagens mais eficientes de armazenamento.

## Leitura relacionada

Para saber mais sobre como gerenciar o espaço em disco (se você estiver no Adobe Commerce na infraestrutura em nuvem), consulte [Gerenciar espaço em disco no Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space.html) no Guia do Commerce na Infraestrutura em Nuvem.
