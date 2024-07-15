---
title: "MDVA-44100: Todos os FPTs são atribuídos ao último produto no carrinho de compras"
description: O patch MDVA-44100 resolve o problema em que todos os FPTs são atribuídos ao último produto no carrinho de compras. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.14 está instalada. A ID do patch é MDVA-44100. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.
exl-id: ab0f195c-fcc6-41ac-932d-d2603d068aa6
feature: Orders, Products, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---

# MDVA-44100: Todos os FPTs são atribuídos ao último produto no carrinho de compras

O patch MDVA-44100 resolve o problema em que todos os FPTs são atribuídos ao último produto no carrinho de compras. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.14 está instalada. A ID do patch é MDVA-44100. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3 - 2.4.4

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Todos os FPTs são atribuídos ao último produto no carrinho de compras e os valores de FPT para o restante dos produtos são redefinidos.

<u>Etapas a serem reproduzidas</u>:

1. Vá para **Lojas** > **Configuração** > **Vendas** > **Imposto** e defina:
   * Ativar FPT = Sim
   * Aplicar Imposto a FPT = Sim
   * Incluir FPT no Subtotal = Sim
1. Vá para **Lojas** > **Atributo** > **Produto** e crie um novo atributo com tipo = Imposto Fixo do Produto.
1. Adicione o atributo a um conjunto de atributos.
1. Crie dois produtos do conjunto de atributos e configure o atributo FPT para seu País e Estado.
1. Adicionar ambos os itens ao pedido.
1. Insira um endereço que exija o pagamento de FPT.
1. Coloque o pedido.
1. Verifique a lista de itens no pedido.

<u>Resultados esperados</u>:

Os FPTs são exibidos sob cada produto.

<u>Resultados reais</u>:

Os valores FPT de ambos os itens são mostrados abaixo do segundo item.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.
