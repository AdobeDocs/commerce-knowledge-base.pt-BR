---
title: "MDVA-34943: o pedido rápido não pode adicionar mais de 2 produtos ao carrinho"
description: O patch MDVA-34943 resolve o problema em que um pedido rápido não pode adicionar dois ou mais produtos ao carrinho. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.17 está instalada. Observe que o problema foi corrigido no Adobe Commerce versão 2.4.2.
exl-id: fcff6a78-fe00-4352-b0bc-149bd411d999
feature: Orders, Products, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '584'
ht-degree: 0%

---

# MDVA-34943: O pedido rápido não pode adicionar mais de 2 produtos ao carrinho

O patch MDVA-34943 resolve o problema em que um pedido rápido não pode adicionar dois ou mais produtos ao carrinho. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.17 está instalada. Observe que o problema foi corrigido no Adobe Commerce versão 2.4.2.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

Adobe Commerce na infraestrutura em nuvem 2.4.0-p1

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce na infraestrutura em nuvem e Adobe Commerce no local 2.3.0 - 2.4.1-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os usuários não conseguem adicionar dois ou mais produtos ao carrinho em ordem rápida.

<u>Pré-requisitos</u>:

Adobe Commerce com produtos simples.

<u>Etapas a serem reproduzidas</u>:

1. Ir para **Pedido Rápido** na Loja (enquanto não estiver conectado).
1. Insira uma SKU válida, clique no produto que aparece no campo preenchimento automático e defina **Quantidade** = *1*.
1. Insira o mesmo SKU válido, mas altere a caixa (altere maiúsculas para minúsculas ou altere minúsculas para maiúsculas) do primeiro caractere, clique no produto que aparece no campo Preenchimento automático e defina **Quantidade** = *1*.
1. Insira um `random_sting_value` para **SKU** e defina **Quantidade** = *1*.
1. Defina **SKU** = *123123123* e defina **Quantidade** = *1*.
1. Exclua tudo, exceto a primeira entrada adicionada à página **Pedido rápido**.
1. Insira o primeiro SKU (semelhante à Etapa 2 acima) no campo **Inserir vários SKUs** e clique em **Adicionar à lista**.
1. Isso resulta em uma quantidade de 2 para o primeiro SKU e uma linha para um `random_sting_value`.
1. Para testar mais, atualize a página.
1. Isso resulta em SKUs sem ordem rápida, conforme esperado.
1. Insira um `random_sting_value2` no campo **Inserir várias SKUs** e clique em **Adicionar à lista**.
1. Isso resulta em duas SKUs válidas de antes e um `random_sting_value2`.

<u>Resultados esperados</u>:

Dois ou mais produtos podem ser adicionados ao carrinho, conforme esperado.

<u>Resultados reais</u>:

Quando levado para a página **Carrinho**, o primeiro produto adicionado aparece normalmente, mas para o segundo produto e qualquer produto subsequente adicionado ao carrinho, é exibida a mensagem de erro &quot;*1 produto requer atenção*&quot;. O segundo produto ou qualquer produto adicional será listado na seção **Produto Requer Atenção** da página **Carrinho**.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte a seção [Patches disponíveis no QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).
