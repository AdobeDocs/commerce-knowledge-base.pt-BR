---
title: "MDVA-35773: O imposto aparece na NFF com desconto de 100%"
description: O patch MDVA-35773 corrige o problema em que o Total geral não é mostrado como zero na fatura para pedidos com um desconto de 100%. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.22 está instalada. A ID do patch é MDVA-35773. Observe que o problema foi corrigido no Adobe Commerce versão 2.4.3.
exl-id: 895cb7d3-be9f-4864-9658-87ee0471f556
feature: Invoices, Marketing Tools, Orders, Personalization, Taxes
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '460'
ht-degree: 0%

---

# MDVA-35773: O imposto aparece na NFF com desconto de 100%

O patch MDVA-35773 corrige o problema em que o Total geral não é mostrado como zero na fatura para pedidos com um desconto de 100%. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.22 está instalada. A ID do patch é MDVA-35773. Observe que o problema foi corrigido no Adobe Commerce versão 2.4.3.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

Adobe Commerce na infraestrutura em nuvem 2.3.6

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce no local e Adobe Commerce na infraestrutura em nuvem 2.3.6-2.3.7 e 2.4.1-2.4.2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

<u>Etapas a serem reproduzidas</u>:

1. Navegue até **Lojas** > **Configurações** > **Configuração** > **Vendas** > **Imposto**.
1. Definir **Preços do catálogo** e **Aplicar desconto sobre preços** a *Incluindo imposto*.
1. Navegue até **Lojas** > **Regras de Imposto** > **Adicionar Nova Regra de Imposto**.
1. Crie uma regra de imposto (Exemplo: todos os EUA com 10% de alíquota do imposto) e aplique-a.
1. Navegue até **Marketing** > **Regras de preço do carrinho** e **Adicionar nova regra**.
1. Crie uma regra com um desconto de **100% para todos os usuários**.
1. Faça um pedido na Loja:

   * Escolha **Envio gratuito**.
   * Aplicar **Código Do Cupom**.

1. Navegue até **Vendas** > **Pedidos** e abra seu pedido.
1. Crie uma fatura para o pedido e abra-a.

<u>Resultados esperados</u>:

O Total Geral da fatura = *$0.00*.

<u>Resultados reais</u>:

O Total Geral da fatura = *valor de imposto* foi criado.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.
