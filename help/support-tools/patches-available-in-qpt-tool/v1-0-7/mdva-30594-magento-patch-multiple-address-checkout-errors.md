---
title: "MDVA-30594: erros de check-out de vários endereços"
description: O patch MDVA-30594 resolve o problema em que o cliente não vê a página de sucesso do pedido após fazer um pedido com vários endereços. Verificar os pedidos no Commerce Admin mostra dois pedidos com os mesmos produtos em vez dos produtos corretos. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 está instalada. O problema foi corrigido no Adobe Commerce 2.4.2.
exl-id: 7560cc39-ff0d-4313-979e-5cd588554c1d
feature: Checkout, Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '644'
ht-degree: 0%

---

# MDVA-30594: erros de check-out de vários endereços

O patch MDVA-30594 resolve o problema em que o cliente não vê a página de sucesso do pedido após fazer um pedido com vários endereços. Verificar os pedidos no Commerce Admin mostra dois pedidos com os mesmos produtos em vez dos produtos corretos. Este patch está disponível quando a variável [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.0.7 está instalado. O problema foi corrigido no Adobe Commerce 2.4.2.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce na infraestrutura em nuvem 2.3.3

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.0 - 2.4.1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Vários pedidos de endereço não são concluídos com a página de sucesso do pedido e mostram dois pedidos com os mesmos produtos em vez dos corretos.

<u>Pré-requisitos</u>:

Crie dois sites com lojas e visualizações de loja.

<u>Etapas a serem reproduzidas</u>:

1. Definir **Escopo do Preço de Catálogo** para o catálogo de sites (**Lojas** > **Configurações** > **Configuração** > **Catálogo** > **Catálogo** > **Preço** > **Escopo**).
1. Configurar **Impostos Fixos sobre Produtos (FPT)** (**Lojas** > **Configuração** > **Vendas** > **Imposto** > **Impostos Fixos sobre Produtos**):

   * **Ativar FPT** = *Sim*
   * **Exibir preços na lista de produtos** = *Excluir FPT*
   * **Exibir Preços na Página de Exibição do Produto** = *Excluir FPT*
   * **Exibir Preços em Módulos de Vendas** = *Excluir FPT* (Incluindo **FPT** descrição e preço final).
   * **Exibir preços em emails** = *Excluir FPT* (Incluindo **FPT** descrição e preço final).
   * **Aplicar Imposto a FPT** = *Sim*
   * **Incluir FPT no Subtotal** = *Não*

1. Criar um **Atributo FPT**, e atribua-o ao conjunto de atributos padrão. (Consulte [Configuração de FPT: Criar um atributo FPT](https://docs.magento.com/user-guide/tax/fixed-product-tax-configuration.html#step-2-create-an-fpt-attribute) no guia do usuário).

1. Crie quatro produtos simples e defina o **FPT** **valor do atributo** (Exemplo: defina a variável **FPT**   **valor do atributo** = *Austrália*).

1. Crie dois produtos agrupados com a seguinte configuração:

   * Definir **FPT**.
   * Definir **Preço dinâmico** = *Não*.
   * Definir **Preço** = *100*.
   * Opções de pacote enviadas juntas, todas marcadas como padrão com **Tipo de preço** = *Fixo*.
   * Adicione dois dos produtos simples criados na Etapa quatro.

1. Crie uma conta de usuário no front-end. Atualize o endereço com o endereço australiano (defina o país como Austrália ou qualquer país que tenha sido usado no **FPT** configuração).

1. Adicione os dois produtos agrupados ao carrinho.

1. Vá para a página do carrinho e verifique se **FPT** O está sendo exibido corretamente.

1. Clique em **Check-out com vários endereços**.

1. Adicione um segundo endereço.

1. Atribua cada produto a um endereço diferente.

1. Prossiga com o processo de finalização até **Fazer pedido**.

1. Clique em **Fazer pedido** botão.

<u>Resultados esperados</u>:

O pedido com vários endereços foi feito com sucesso.

<u>Resultados reais</u>:

Uma mensagem como, &quot;*Erro.*&quot; aparecerá.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de atualização de software > Aplicar patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatendimento de correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de patches de qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.
