---
title: "MDVA-35197: erro de adição ao carrinho do GraphQL se produtos adicionados estiverem indisponíveis"
description: O patch MDVA-35197 corrige o problema em que há um erro ao adicionar ao carrinho usando o GraphQL se os produtos adicionados anteriormente ficarem indisponíveis. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.17 está instalada.
exl-id: 189312f7-a505-4ba4-b12d-662987e69374
feature: GraphQL, Orders, Products, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---

# MDVA-35197: erro de adição ao carrinho do GraphQL se produtos adicionados estiverem indisponíveis

O patch MDVA-35197 corrige o problema em que há um erro ao adicionar ao carrinho usando o GraphQL se os produtos adicionados anteriormente ficarem indisponíveis. Este patch está disponível quando a variável [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.0.17 está instalado.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

Adobe Commerce na infraestrutura em nuvem 2.3.6

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.3.5 - 2.3.6-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Erro ao tentar adicionar um produto ao carrinho por meio do GraphQL se o outro produto já no carrinho (também adicionado por meio do GraphQL) ficar indisponível.

<u>Etapas a serem reproduzidas</u>:

1. Usando o GraphQL, adicione qualquer produto ao carrinho.
1. Faça logon no painel Admin do Commerce e defina este produto como esgotado.
1. Tente adicionar outro produto ao carrinho por meio do GraphQL.

<u>Resultados esperados</u>:

Os produtos em estoque podem ser adicionados ao carrinho.

<u>Resultados reais</u>:

Mensagem de erro do GraphQL: *Alguns dos produtos estão esgotados*. Não é possível adicionar um novo produto &quot;em estoque&quot;.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de atualização de software > Aplicar patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatendimento de correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de patches de qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.
