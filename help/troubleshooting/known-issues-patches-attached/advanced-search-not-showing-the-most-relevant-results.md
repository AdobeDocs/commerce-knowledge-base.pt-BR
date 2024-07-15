---
title: A pesquisa avançada não mostra os resultados mais relevantes
description: Este artigo fornece uma correção para o problema conhecido do Adobe Commerce, em que a Pesquisa avançada não mostra os resultados mais relevantes primeiro.
exl-id: 88f0782d-ba7d-4f19-9761-7894d978d334
feature: Search
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 0%

---

# A pesquisa avançada não mostra os resultados mais relevantes

Este artigo fornece uma correção para o problema conhecido do Adobe Commerce, em que a Pesquisa avançada não mostra os resultados mais relevantes primeiro.

## Versões afetadas {#Advancedsearchnotshowingmostrelevantresults-Affectedversions}

* Adobe Commerce (todas as opções de implantação) 2.x.x
* Magento Open Source 2.x.x

## Problema {#Advancedsearchnotshowingmostrelevantresults-Description}

A função de pesquisa avançada não retorna os resultados mais relevantes primeiro, como a pesquisa rápida está fazendo. O problema não depende do tipo de mecanismo de pesquisa selecionado.

<u>Etapas a serem reproduzidas:</u>

1. Na loja, acesse a pesquisa rápida e pesquise por &quot;Jaqueta Adaptada&quot;.
1. Observe que &quot;Orion Two-Tone Fitted Jacket&quot; é o primeiro resultado.
1. Vá para a pesquisa avançada e pesquise por &quot;Jaqueta Adaptada&quot; no campo de nome.

<u>Resultado esperado:</u>

O &quot;Orion Two-Tone Fitted Jacket&quot; é o primeiro resultado ao usar a pesquisa avançada, como o resultado mais relevante.

<u>Resultado real:</u>

O &quot;Orion Two-Tone Fitted Jacket&quot; não é o primeiro resultado, embora seja o mais relevante.

## Solução {#Advancedsearchnotshowingmostrelevantresults-Solution}

Para resolver o problema, aplique o patch anexado a este artigo. Para baixá-lo, role para baixo até o final do artigo e clique no nome do arquivo ou clique no link a seguir:

[Baixar MDVA-7256\_EE\_2.1.7\_v1.composer.patch](assets/MDVA-7256_EE_2.1.7_v1.composer.patch.zip)

O patch adiciona a implementação para classificação por relevância dos resultados de pesquisa avançada como o campo de classificação padrão.

O patch é compatível com todas as versões e edições afetadas.

## Como aplicar o patch

Para obter instruções, consulte [Como aplicar um patch de compositor fornecido pelo Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) em nossa base de dados de conhecimento de suporte.

## Arquivos anexados
