---
title: "MDVA-30837: valor mínimo do pedido para frete grátis"
description: O patch MDVA-30837 adiciona opções de configuração para o cálculo de frete gratuito para que o usuário possa configurar a Quantidade mínima do pedido para obter frete gratuito com base no Subtotal (ou Total geral). Isso permite personalizações locais para métodos de imposto e envio. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 está instalada. Observe que o problema foi corrigido no Adobe Commerce 2.4.2.
exl-id: 64716d08-4ce0-40d5-aeb7-242e2aa85bb0
feature: Marketing Tools, Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '701'
ht-degree: 0%

---

# MDVA-30837: valor mínimo de pedido para frete grátis

O patch MDVA-30837 adiciona opções de configuração para o cálculo de frete gratuito para que o usuário possa configurar a Quantidade mínima do pedido para obter frete gratuito com base no Subtotal (ou Total geral). Isso permite personalizações locais para métodos de imposto e envio. Este patch está disponível quando a variável [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.0.7 está instalado. Observe que o problema foi corrigido no Adobe Commerce 2.4.2.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce na infraestrutura em nuvem 2.3.4-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce na infraestrutura em nuvem 2.3.1 - 2.3.4-p2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O patch MDVA-30837 adiciona a definição de configuração para definir o **Valor Mínimo do Pedido** configuração para obter frete grátis com base no Subtotal (ou Total geral):

* **Incluir Imposto no Valor**: *Sim/Não* na configuração do método de envio gratuito.
   * Quando **Incluir Imposto no Valor** está definida como *Sim*, o valor mínimo do pedido é calculado como Subtotal + Imposto - Desconto.
   * Quando **Incluir Imposto no Valor** está definida como *Não*, o valor mínimo do pedido é calculado como Subtotal - Desconto.

<u>Etapas a serem reproduzidas</u>:

1. Ir para **Lojas** > Configurações > **Configuração** > **Vendas** > **Imposto** e defina o seguinte:

   * Cálculo do Imposto Baseado em *Endereço de entrega*
   * Ativar comércio transfronteiriço: *Não*
   * Exibir Preços de Produção no Catálogo: *Excluindo Imposto*
   * Exibir preços de envio: *Excluindo Imposto*
   * Exibir preços: *Excluindo Imposto*
   * Exibir Subtotal: *Excluindo Imposto*
   * Exibir Valor da Remessa: *Excluindo Imposto*
   * Exibir preços de quebra de presente: *Excluindo Imposto*
   * Exibir preços de cartão impresso: *Excluindo Imposto*
   * Incluir imposto no total do pedido: *Sim*
   * Exibir Sumário de Imposto Completo: *Sim*

1. Ir para **Vendas** > **Configurações de envio** > **Envio gratuito** e defina **Valor Mínimo do Pedido** = *30*.
1. Ir para **Marketing** > Promoções > **Regras de preço do carrinho** e criar uma nova regra de preço (para obter etapas detalhadas, consulte [Criar uma regra de preço do carrinho](https://docs.magento.com/user-guide/marketing/price-rules-cart-create.html) no guia do usuário).

   * Código Do Cupom = *Cupom Específico*.
   * Condições: Subtotal igual ou maior que US$ 25.
   * Ações: envio gratuito = *Para entregas com itens correspondentes*.

1. Crie um produto com um preço de US$ 23,10.
1. Adicione o imposto CA à regra de imposto padrão.
1. Adicionar este produto ao carrinho.
1. Obtenha uma cotação de remessa - após impostos, o Total geral = US$ 25,01 e o frete grátis é aplicado.
1. Aplique o código do cupom - ele não será válido porque o Subtotal (Excluindo Imposto) é de $23,10.

<u>Resultados esperados</u>:

Há uma definição de configuração adicional - Incluir Imposto na Quantia: *Sim*/*Não* na configuração do método de envio gratuito:

* Quando Incluir Imposto no Valor estiver definido como *Sim*, a Quantia Mínima do Pedido é calculada como Subtotal + Imposto - Desconto.
* Quando Incluir Imposto no Valor estiver definido como *Não*, a Quantia Mínima do Pedido é calculada como Subtotal - Desconto.

<u>Resultados reais</u>:

A condição da regra de preço de Frete Gratuito só pode ser baseada no Subtotal, enquanto o método de Frete Gratuito só pode ser baseado no Total Geral.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de atualização de software > Aplicar patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatendimento de correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de patches de qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.
