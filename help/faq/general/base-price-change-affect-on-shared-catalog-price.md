---
title: Alteração de preço base afeta no preço de catálogo compartilhado
description: 'Este artigo responde à pergunta: se um produto em um catálogo compartilhado tiver um preço personalizado e o preço base do produto mudar (por exemplo, após uma atualização programada), qual preço se aplica ao catálogo compartilhado?'
exl-id: 916678c1-ada6-4f23-af16-b107cb83ff16
feature: Catalog Management
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 0%
---
# Alteração de preço base afeta no preço de catálogo compartilhado

Este artigo responde à pergunta: se um produto em um catálogo compartilhado tiver um preço personalizado e o preço base do produto mudar (por exemplo, após uma atualização programada), qual preço se aplica ao catálogo compartilhado?

## Com o preço personalizado definido como Porcentagem, o preço do catálogo compartilhado também muda

Se o preço personalizado de um produto em um catálogo compartilhado tiver sido definido como Porcentagem, o preço do catálogo compartilhado do produto será atualizado implicitamente após a alteração do preço base.

Em outras palavras, quando o preço base é atualizado (por meio de uma atualização normal ou programada), o preço de catálogo compartilhado também muda após a aplicação do desconto percentual.

## Com preço personalizado definido como Fixo, o preço do catálogo compartilhado não é alterado

Se o preço personalizado de um produto em um catálogo compartilhado tiver sido definido como Fixo, o preço no catálogo compartilhado nunca será alterado, independentemente da maneira como atualizamos o preço base (por meio de atualização programada, Adobe Commerce Admin, API ou importação).

## A loja sempre exibe o menor preço disponível

Se o preço base do produto mudar e se tornar menor que o preço correspondente do catálogo compartilhado, a Loja exibirá o preço base como o preço mais baixo disponível no sistema.

## Leitura relacionada

[Definir preços e estrutura para um catálogo compartilhado](https://experienceleague.adobe.com/docs/commerce-admin/b2b/shared-catalogs/define/catalog-shared-pricing-structure.html?lang=pt-BR) em nosso guia do usuário.
