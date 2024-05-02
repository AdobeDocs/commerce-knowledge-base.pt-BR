---
title: Amostras de produto configuráveis não exibidas riscadas quando fora de estoque
description: Este artigo fornece um patch para o problema conhecido do Adobe Commerce 2.2.2 relacionado ao fato de as amostras de produtos configuráveis não serem exibidas como riscadas na loja.
exl-id: 79c59a3f-a94b-4726-8af1-5fe754ea95a5
feature: Configuration, Orders, Products
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 0%

---

# Amostras de produto configuráveis não exibidas riscadas quando fora de estoque

Este artigo fornece um patch para o problema conhecido do Adobe Commerce 2.2.2 relacionado ao fato de as amostras de produtos configuráveis não serem exibidas como riscadas na loja.

## Problema

Quando você tem um produto configurável e, para uma determinada combinação de opções, o produto simples relacionado está esgotado, a amostra ainda está disponível e pode ser selecionada na loja.

<u>Etapas a serem reproduzidas</u>:

1. No Commerce Admin, crie um produto configurável com opções para dois atributos: cor (vermelho, preto) e tamanho (S, M, L).
1. Defina a Quantidade como &quot;1&quot; para cada produto simples correspondente.
1. Na loja, adicione o produto M vermelho ao carrinho e ao checkout.
1. No Administrador, processe o pedido para que a quantidade do item seja atualizada para &quot;0&quot;.
1. Certifique-se de que as ordens pendentes não sejam permitidas.
1. Na loja, navegue até a mesma página de produto e selecione as mesmas opções: vermelho, M.

<u>Resultados esperados</u>:

A amostra vermelha, M tem uma barra vermelha e não pode ser selecionada.

<u>Resultados reais</u>:

A amostra vermelha, M pode ser selecionada.

## Correção

O patch está anexado a este artigo. Para baixá-lo, role para baixo até o final do artigo e clique no nome do arquivo ou clique no link a seguir:

[Baixar MDVA-8215\_EE\_2.2.2\_v1.composer.patch](assets/MDVA-8215_EE_2.2.2_v1.composer.patch.zip)

### Versões compatíveis do Adobe Commerce:

A correção foi criada para:

* Adobe Commerce (todos os métodos de implantação) 2.2.2

O patch também é compatível (mas pode não resolver o problema) com as seguintes versões e edições do Adobe Commerce:

* Adobe Commerce no local e Adobe Commerce na infraestrutura em nuvem 2.2.0-2.2.3

## Como aplicar o patch

Consulte [Como aplicar um patch de compositor fornecido pelo Adobe Commerce](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) para obter instruções.

## Arquivos Anexados
