---
title: "MDVA-43605: os dados da ordem retornam valores negativos para os totais das linhas ao usar a API Rest"
description: O patch MDVA-43605 corrige o problema em que os dados do pedido retornam valores negativos para totais de linha ao usar a API Rest. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.14 está instalada. A ID do patch é MDVA-43605. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.
exl-id: 8a679e85-1681-42c3-b072-18797198bdc4
feature: REST, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '549'
ht-degree: 0%

---

# MDVA-43605: os dados da ordem retornam valores negativos para totais de linha ao usar a API Rest

O patch MDVA-43605 corrige o problema em que os dados do pedido retornam valores negativos para totais de linha ao usar a API Rest. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.14 está instalada. A ID do patch é MDVA-43605. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.1 - 2.4.4

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os dados do pedido retornam valores negativos para totais de linha ao usar a API Rest.

<u>Etapas a serem reproduzidas</u>:

1. Ativar frete gratuito.
1. Navegue até **Configuração** > **Catálogo** > **Preço** > e defina Escopo do Preço do Catálogo = Site.
1. Navegue até **Configuração** > **Vendas** > **Imposto** e atualize:
   * Classe De Imposto Para Entrega = Mercadorias Tributáveis
   * Configurações de Cálculo:
      * Preço do Catálogo = Imposto Incluído
      * Preço de Entrega = Preço Incluído
      * Aplicando Desconto em Preços = Incluindo Imposto
   * Configurações de Exibição de Preço: Incluindo Imposto (todos os campos)
   * Configurações de exibição do carrinho de compras: incluindo imposto (todos os campos)
   * Ordens, NFFs, Avisos de Crédito:
      * Exibir Quantia de Entrega = Imposto Incluído
1. Criar uma alíquota de imposto para os EUA (Estado = &#39;*&#39;), Percentual da Taxa = 24,00
1. Crie uma Regra de Imposto com a Alíquota de Imposto acima.
1. Crie uma regra de preço do carrinho com um cupom específico e Desconto = US$ 50 do Valor fixo para todo o carrinho.
1. Crie quatro produtos com os seguintes preços: $ 8,90, $ 5,90, $ 6,90 e $ 5,95.
1. Crie um pedido de administrador incluindo quatro desses produtos usando o código do cupom criado na etapa anterior. Use o frete grátis.
1. O pagamento não deve ser necessário, pois o código do cupom cobre o total do carrinho.
1. Recupere o pedido que acabou de ser criado por meio do ponto de extremidade da API Rest:

   ```json
   GET rest/V1/orders/1
   ```

<u>Resultados esperados</u>:

Os valores de `base_row_total` e `base_row_total_incl_tax` na resposta são zero.

<u>Resultados reais</u>:

Os campos `base_row_total` e `base_row_total_incl_tax` na resposta têm valores negativos.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.
