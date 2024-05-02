---
title: '[!DNL Live Search] exibe produtos indisponíveis, independentemente das configurações de status do estoque no admin'
description: Este artigo fornece informações sobre o problema conhecido em que a Página de listagem de produtos (PLP) mostra o erro *Não é possível encontrar produtos que correspondam à seleção*, enquanto o popover de pesquisa retorna alguns itens.
exl-id: 2a351b83-407c-444a-a761-4932b5b88843
feature: Admin Workspace, Categories, Orders, Products, Search
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 0%

---

# [!DNL Live Search] exibe produtos indisponíveis, independentemente das configurações de status do estoque no admin

>[!IMPORTANT]
>
>Este problema foi corrigido no [[!DNL Live Search] [2.0.4]](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/release-notes.html). Para instalar a versão mais recente, consulte [Atualizando [!DNL Live Search]](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html#update) no guia do usuário.

Este artigo fornece informações sobre o problema conhecido em que a PLP (Página de listagem de produtos) mostra a *Não conseguimos encontrar produtos que correspondam à seleção* erro enquanto o popover de pesquisa retorna alguns itens.

## Produtos e versões afetados

Adobe Commerce (todos os métodos de implantação) 2.4.x

## Problema

[!DNL Live Search] O exibe os resultados da pesquisa independentemente das configurações de status do estoque no Administrador do Adobe Commerce. Mesmo quando a variável **[!UICONTROL Display Out-of-Stock Products]** está definida como *Não*, os produtos são exibidos. Isso resulta no erro PLP *Não conseguimos encontrar produtos que correspondam à seleção*.

<u>Etapas a serem reproduzidas</u>:

1. Crie uma categoria, adicione produtos. (Exemplo: Categoria = _Jeans_, Produto1 = _Blue Jeans_, Produto2 = _Black Jeans_)
1. Deixe todos os produtos da categoria esgotados.
1. Definir **[!UICONTROL Display Out-of-Stock Products]** para *Não*.
1. Na loja, insira *Jeans* no campo de pesquisa.
1. Clique em **[!UICONTROL View All]** na janela pop-up.

<u>Resultado esperado</u>:

Você vê a *Não conseguimos encontrar produtos que correspondam à seleção* e nenhum produto é exibido na janela pop-up de pesquisa.

<u>Resultado real</u>:

Você vê a *Não conseguimos encontrar produtos que correspondam à seleção* e ambos os produtos são exibidos na janela pop-up de pesquisa.

## Solução

Não há solução para esse problema no momento. Nosso [!DNL Live Search] em breve, a equipe fornecerá uma configuração para definir [!DNL Live Search] para exibir os produtos corretamente.

## Leitura relacionada

[Instalar [!DNL Live Search]](https://docs.magento.com/user-guide/live-search/install.html) em nosso guia do usuário.
