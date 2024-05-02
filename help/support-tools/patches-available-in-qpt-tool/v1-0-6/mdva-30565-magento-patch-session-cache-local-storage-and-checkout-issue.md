---
title: "MDVA-30565: problema de armazenamento local e check-out no cache da sessão"
description: O patch MDVA-30565 resolve o problema com o armazenamento local do cache da sessão e a finalização. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6 está instalada.
exl-id: f0693f0c-fc6b-44af-a6a0-ebfa973bca65
feature: Cache, Checkout, Orders, Storage
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '470'
ht-degree: 0%

---

# MDVA-30565: problema de armazenamento local e check-out no cache da sessão

O patch MDVA-30565 resolve o problema com o armazenamento local do cache da sessão e a finalização. Este patch está disponível quando a variável [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.0.6 está instalado.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce na infraestrutura em nuvem 2.3.3-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.2 - 2.3.3-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os itens do carrinho ainda podem ser vistos na página do carrinho quando a sessão do cliente atinge o tempo limite. Isso causa um erro do método de envio estimado em que nenhum método de envio está disponível para check-out de convidado.

<u>Etapas a serem reproduzidas</u>:

1. Ative o carrinho de compras persistentes no Administrador do Commerce. (**Ativar persistência** = &quot;*Sim*&quot;)
1. Faça logon como cliente no front-end. Isso cria o `persistent_shopping_cart` cookie e inicia uma sessão persistente.
1. Adicione um produto ao carrinho.
1. Aguarde até que a sessão de front-end atinja o tempo limite ou exclua o `PHPSESSID` cookie.
1. Agora, você é um usuário convidado, mas se for ao carrinho, ainda poderá ver o produto que foi adicionado como cliente conectado.
1. Remova o produto do carrinho e agora o carrinho está vazio. Você pode ver o Adobe Commerce excluir o `persistent_shopping_cart` cookie neste evento.
1. Adicione um novo produto ao carrinho e vá para a página do carrinho.
1. Agora, no console do navegador, ele aparece `V1/guest-carts/4/estimate-shipping-methods` request now retorna uma resposta 404 com mensagem `{"message":"No such entity        with %fieldName = %fieldValue","parameters":{"fieldName":"cartId","fieldValue":0}}`

<u>Resultados esperados</u>:

A solicitação do método de envio estimado retorna os resultados corretos.

<u>Resultados reais</u>:

A solicitação do método de envio estimado falha com um erro como, &quot;*Não há cotações disponíveis para este pedido no momento.*&quot;

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de atualização de software > Aplicar patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatendimento de correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de patches de qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.
