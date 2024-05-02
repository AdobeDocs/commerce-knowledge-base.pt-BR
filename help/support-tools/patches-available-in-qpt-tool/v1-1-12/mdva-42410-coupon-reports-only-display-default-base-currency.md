---
title: "MDVA-42410: os relatórios de cupom exibem somente a moeda base padrão"
description: O patch MDVA-42410 corrige o problema em que os relatórios de cupom exibem apenas a moeda base. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 está instalada. A ID do patch é MDVA-42410. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.
exl-id: b442a2ce-1bd4-4f09-95fd-2c626e32f509
feature: Orders
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# MDVA-42410: os relatórios de cupom exibem somente a moeda base padrão

O patch MDVA-42410 corrige o problema em que os relatórios de cupom exibem apenas a moeda base. Este patch está disponível quando a variável [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.12 está instalado. A ID do patch é MDVA-42410. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os relatórios de cupom exibem somente a moeda base padrão.

<u>Etapas a serem reproduzidas</u>:

1. Crie um Site, Loja e Exibição de Loja adicionais.
1. Defina uma moeda diferente para este novo site. Por exemplo, Euro.
1. Ir para **Lojas** > **Taxas de câmbio** e configurar taxas de moeda para **Euro**.
1. Criar um **Regra de preço do carrinho** com um cupom específico - **Teste**.
1. Vá para o front-end e faça um pedido com a **Teste** cupom no novo site.
1. Ir para **Relatórios** > **Vendas** > **Cupons**.
1. Selecione o novo site na lista suspensa Escopo.
1. Atualizar estatísticas e executar relatórios.

<u>Resultados esperados</u>:

Os relatórios de cupom exibem a moeda do novo site como Euro.

<u>Resultados reais</u>:

A moeda base padrão (USD, neste caso) é usada em relatórios de cupom para o novo site.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de atualização de software > Aplicar patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatendimento de correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de patches de qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.
