---
title: "MDVA-31763: as regras de preço do catálogo são revertidas até a reindexação manual"
description: O patch MDVA-31763 resolve o problema em que as regras de preço do catálogo são revertidas até a reindexação manual. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.5 está instalada. A ID do patch é MDVA-31763. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.
exl-id: eb2dfd1a-6d12-4676-82c1-bf92c6fa9fda
feature: Catalog Management, Orders, Price Rules
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '490'
ht-degree: 0%

---

# MDVA-31763: as regras de preço do catálogo são revertidas até a reindexação manual

O patch MDVA-31763 resolve o problema em que as regras de preço do catálogo são revertidas até a reindexação manual. Este patch está disponível quando a variável [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.5 está instalado. A ID do patch é MDVA-31763. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.5-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Quando `catalogrule_product` o indexador parcial é executado em produtos configuráveis, as regras de catálogo desaparecem.

<u>Etapas a serem reproduzidas</u>:

1. Faça logon no back-end do Administrador.
1. Ir para **Lojas** > **Atributos** > **Produto** e procure pelo atributo &quot;fabricante&quot;.
   * Adicione algumas opções e defina &quot;Usar para condições de regra promocional&quot; como *Sim*.
1. Ir para **Lojas** > **Atributos** > **Conjuntos de atributos**.
   * Selecione o conjunto de atributos padrão e adicione o atributo &quot;fabricante&quot; a ele.
1. Crie um produto configurável com algumas variações.
1. Defina o valor do atributo &quot;fabricante&quot; para o produto configurável criado anteriormente.
1. Criar regras de catálogo:
   * Ativo = Sim
   * Sites = Site Principal
   * Grupos de Clientes = NÃO CONECTADO
   * Condições: fabricante = \&lt;selected value=&quot;&quot; for=&quot;&quot; configurable=&quot;&quot; product=&quot;&quot;>
   * Ações: Qualquer desconto
1. Fazer um índice completo.
1. Verifique o preço do produto no PDP e certifique-se de que o preço esteja correto.
1. Atualize o atributo &quot;weight&quot; do produto configurável criado.
1. Verifique o preço do produto no PDP.

<u>Resultados esperados</u>:

As regras de preço de catálogo definidas nos produtos configuráveis não são removidas durante a reindexação parcial.

<u>Resultados reais</u>:

As regras de preço de catálogo definidas em produtos configuráveis desaparecem durante a reindexação parcial.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de atualização de software > Aplicar patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatendimento de correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de patches de qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte o [Patches disponíveis no QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) seção.
