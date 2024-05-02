---
title: "MDVA-40488: produtos configuráveis com produtos secundários indisponíveis não mostrados na faixa de preço correta"
description: O patch MDVA-40488 resolve o problema em que os produtos configuráveis com produtos secundários esgotados não são mostrados em sua faixa de preço correta. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9 está instalada. A ID do patch é MDVA-40488. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.
exl-id: 0c4b9f5e-ae41-409e-b244-1d7cf948ed6f
feature: Configuration, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '591'
ht-degree: 0%

---

# MDVA-40488: produtos configuráveis com produtos secundários indisponíveis não mostrados na faixa de preço correta

O patch MDVA-40488 resolve o problema em que os produtos configuráveis com produtos secundários esgotados não são mostrados em sua faixa de preço correta. Este patch está disponível quando a variável [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.9 está instalado. A ID do patch é MDVA-40488. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os produtos configuráveis com produtos secundários indisponíveis não são mostrados em sua faixa de preço correta.

<u>Pré-requisitos</u>:

Acesse o Administrador do Commerce > **lojas** > **configuração** > **catálogo** > **Inventário** > **opções de ações** e defina **Exibir Produtos sem Estoque** configuração para *Sim*.

<u>Etapas a serem reproduzidas</u>:

1. Crie um produto configurável com dois produtos associados. Por exemplo: produtos simples Vermelho e Marrom.
1. Defina o estoque do produto simples como Vermelho e defina Status do Estoque como *Em estoque*, em seguida, defina o status Ativar produto para *Não*.
1. Defina o inventário do produto simples Brown e o status Habilitar produto como *Sim*.
1. Verifique se o status do estoque do produto configurável é *Em estoque*.
1. Alterar o estoque do produto simples Brown para 0 e definir o Status do Estoque como *Sem estoque*.
1. Neste ponto, o Status do estoque do produto configurável ainda é *Em estoque*.
1. Executar reindexação.
1. Verifique a `min_price` e `max_price` para o produto configurável no `catalog_product_index_price` Tabela DB - os dois valores são definidos como 0.
1. Mas se definirmos o Status do estoque do produto configurável como *Sem estoque* e reindexar, então podemos ver diferente de zero `min_price` e `max_price` valores do produto configurável.

<u>Resultados esperados</u>:

Se todos os produtos derivados forem *Sem estoque* e o próprio produto configurável também é *Sem estoque*, o preço é calculado usando todos os produtos secundários.

<u>Resultados reais</u>:

A variável `min_price` e `max_price` valores para o produto configurável no `catalog_product_index_price` As tabelas do banco de dados são definidas como 0 quando o status do estoque configurável é *Em estoque*, mas se for *Sem estoque* eles se tornam valores diferentes de zero.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de atualização de software > Aplicar patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatendimento de correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de patches de qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.
