---
title: "MDVA-40609: Dados de produtos desabilitados ausentes na tabela cataloginventory_stock_status"
description: O patch MDVA-40609 resolve o problema em que os dados de produtos desativados não são mostrados na tabela de índice "cataloginventory_stock_status", resultando na exibição de quantidades de produtos incorretas. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.6 está instalada. A ID do patch é MDVA-40609. Observe que o problema foi corrigido no Adobe Commerce 2.4.3.
exl-id: 2424c3b3-8bc9-4dd4-908c-9d653f09a57a
feature: Catalog Management, Inventory, Orders, Products
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# MDVA-40609: Dados de produtos desabilitados ausentes na tabela cataloginventory_stock_status

O patch MDVA-40609 resolve o problema em que os dados dos produtos desativados não são mostrados no `cataloginventory_stock_status` tabela de índice que exibe quantidades de produto incorretas. Este patch está disponível quando a variável [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.6 está instalado. A ID do patch é MDVA-40609. Observe que o problema foi corrigido no Adobe Commerce 2.4.3.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2 - 2.4.2-p2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os dados de produtos desativados não são mostrados na `cataloginventory_stock_status` tabela de índice que exibe quantidades de produto incorretas.

<u>Pré-requisitos</u>:

O módulo de inventário está instalado.

<u>Etapas a serem reproduzidas</u>:

1. Configure dois sites com lojas e visualizações de loja.
1. Criar uma fonte e um estoque adicionais.
1. Adicione um produto simples:
   * Definir habilitar produto para *Não*.
   * Atribua duas origens com Status do Item de Origem = Instock e Qtd. maior que zero.
1. Salve o produto.
1. Verifique a **Quantidade de Produtos Venáveis** guia.

<u>Resultados esperados</u>:

Ambos os estoques inseriram valores maiores que zero.

<u>Resultados reais</u>:

Um estoque tem valor zero.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de atualização de software > Aplicar patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatendimento de correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de patches de qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte o [Patches disponíveis no QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) seção.
