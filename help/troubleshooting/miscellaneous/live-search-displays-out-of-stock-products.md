---
title: '[!DNL Live Search] exibe produtos indisponíveis, independentemente das configurações de status do estoque no administrador'
description: Este artigo fornece informações sobre o problema conhecido em que a Página de listagem de produtos (PLP) mostra o erro *Não é possível encontrar produtos que correspondam à seleção*, enquanto o popover de pesquisa retorna alguns itens.
exl-id: 2a351b83-407c-444a-a761-4932b5b88843
feature: Admin Workspace, Categories, Orders, Products, Search
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 0%

---

# [!DNL Live Search] exibe produtos indisponíveis, independentemente das configurações de status do estoque no administrador

>[!IMPORTANT]
>
>Este problema foi corrigido em [[!DNL Live Search] [2.0.4]](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/release-notes.html). Para instalar a versão mais recente, consulte [Atualizando [!DNL Live Search]](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html#update) no guia do usuário.

Este artigo fornece informações sobre o problema conhecido em que a PLP (Página de Listagem de Produtos) mostra o erro *Não é possível encontrar produtos que correspondam à seleção*, enquanto o popover de pesquisa retorna alguns itens.

## Produtos e versões afetados

Adobe Commerce (todos os métodos de implantação) 2.4.x

## Problema

[!DNL Live Search] exibe os resultados da pesquisa independentemente das configurações de status do estoque no Administrador do Adobe Commerce. Mesmo quando o **[!UICONTROL Display Out-of-Stock Products]** está definido como *Não*, os produtos são exibidos. Isso resulta no erro de PLP *Não é possível encontrar produtos que correspondam à seleção*.

<u>Etapas a serem reproduzidas</u>:

1. Crie uma categoria, adicione produtos. (Exemplo: Categoria = _Jeans_, Produto1 = _Blue Jeans_, Produto2 = _Black Jeans_)
1. Deixe todos os produtos da categoria esgotados.
1. Defina **[!UICONTROL Display Out-of-Stock Products]** como *Não*.
1. Na vitrine, digite *Jeans* no campo de pesquisa.
1. Clique em **[!UICONTROL View All]** na janela pop-up.

<u>Resultado esperado</u>:

Você vê a mensagem *Não é possível encontrar produtos que correspondam à seleção* no PLP e nenhum produto é exibido no pop-up de pesquisa.

<u>Resultado real</u>:

Você vê a mensagem *Não é possível encontrar produtos que correspondam à seleção* no PLP, e ambos os produtos são exibidos no pop-up de pesquisa.

## Solução

Não há solução para esse problema no momento. Nossa equipe do [!DNL Live Search] em breve fornecerá uma configuração para configurar o [!DNL Live Search] para exibir produtos corretamente.

## Leitura relacionada

[Instalar [!DNL Live Search]](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/live-search/install) em nosso guia do usuário.
