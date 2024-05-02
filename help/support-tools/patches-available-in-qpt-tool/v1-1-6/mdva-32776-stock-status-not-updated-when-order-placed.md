---
title: "MDVA-32776: status do estoque não atualizado com o posicionamento do pedido"
description: O patch MDVA-32776 corrige o problema em que o status do estoque não é atualizado quando um pedido é feito, mas não enviado. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.6 está instalada. A ID do patch é MDVA-32776. Observe que o problema foi corrigido no Adobe Commerce 2.4.2.
exl-id: 10e9458f-562a-480b-b813-104a93db4308
feature: Orders
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 0%

---

# MDVA-32776: Status do estoque não atualizado com posicionamento do pedido

O patch MDVA-32776 corrige o problema em que o status do estoque não é atualizado quando um pedido é feito, mas não enviado. Este patch está disponível quando a variável [Ferramenta de correções de qualidade (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) O 1.1.6 está instalado. A ID do patch é MDVA-32776. Observe que o problema foi corrigido no Adobe Commerce 2.4.2.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.4.0

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.4.0 - 2.4.1-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O status do estoque não é atualizado quando um pedido é feito, mas não enviado.

<u>Pré-requisitos</u>:

1. O módulo de inventário está instalado.
1. Exibir produtos indisponíveis está definido como *Sim*.

   Para definir, acesse **Lojas** > **Configuração** > **Catálogo** > **Inventário** > **Exibir produtos indisponíveis** = *Sim*.

<u>Etapas a serem reproduzidas</u>:

1. Crie dois produtos simples com quantidade = 11 e 22.
1. Crie um produto agrupado usando os produtos simples criados na etapa um.
1. Adicione produtos agrupados ao carrinho definindo uma da quantidade de produtos como 11 e fazendo com que o outro produto simples fique indisponível.
1. Conclua a finalização e faça o pedido.

<u>Resultados esperados</u>:

Exibição de produtos agrupados `out-of-stock` rótulos quando produtos simples associados saem do estoque.

<u>Resultados reais</u>:

1. O produto simples com qtd. = 11 mostra o produto esgotado.
1. O produto agrupado não mostra uma *esgotado* mensagem para o produto com quantidade = 11. No entanto, adicionar esse produto ao carrinho fornece uma *esgotado* erro.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de atualização de software > Aplicar patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatendimento de correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de patches de qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte o [Patches disponíveis no QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) seção.
