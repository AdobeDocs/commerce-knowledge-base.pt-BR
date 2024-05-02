---
title: "Patch MDVA-31363: a regra de preço do carrinho não se aplica (GraphQL)"
description: O patch MDVA-31363 corrige o problema em que a regra de preço do carrinho com cupom não se aplica por meio do GraphQL quando a ação "Desconto de valor fixo para carrinho inteiro" é usada. Este patch está disponível quando a Ferramenta de correções de qualidade (QPT) 1.0.9 está instalada. O problema está programado para ser corrigido no Adobe Commerce versão 2.4.2.
exl-id: f64fbbb1-b5fd-4624-bcdd-d1e6c1f9acfe
feature: GraphQL, Orders, Price Rules, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 0%

---

# Patch MDVA-31363: a regra de preço do carrinho não se aplica (GraphQL)

>[!WARNING]
>
>Um novo patch chamado MDVA-33975 corrige problemas de cálculo de preço do GraphQL. O MDVA-31363 está depreciado e recomenda-se a aplicação do patch MDVA-33975. Para acessar este patch, consulte [Correção do MDVA-33975: cálculos de preço do GraphQL](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/mdva-33975-magento-patch-graphql-price-calculations.html).

O patch MDVA-31363 corrige o problema em que a regra de preço do carrinho com cupom não se aplica por meio do GraphQL quando a ação &quot;Desconto de valor fixo para carrinho inteiro&quot; é usada. Este patch está disponível quando a variável [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.0.9 está instalado. O problema está programado para ser corrigido no Adobe Commerce versão 2.4.2.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

Adobe Commerce na infraestrutura em nuvem 2.4.0

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce na infraestrutura em nuvem e Adobe Commerce no local 2.3.2 - 2.4.1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Recalcular totais de cota antes de dar uma resposta sobre preços de cota causa a perda das regras aplicadas.

<u>Etapas a serem reproduzidas</u>:

1. Crie um produto simples.
1. Crie uma regra de preço do carrinho com um desconto de valor fixo para todo o carrinho.
1. Crie um novo carrinho de compras usando o GraphQL.
1. Salve o card\_id da resposta e adicione o produto da etapa 1 ao carrinho usando o GraphQL.
1. Ative a regra de preço do carrinho adicionando o código do cupom ao carrinho usando o GraphQL.
1. Verificar preço em resposta.

<u>Resultados esperados</u>:

Desconto aplicado.

<u>Resultados reais</u>:

O desconto não é aplicado.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de atualização de software > Aplicar patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatendimento de correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de patches de qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte o [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.
