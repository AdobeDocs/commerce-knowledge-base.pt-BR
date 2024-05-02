---
title: "MDVA-42969: a regra de produto relacionada funciona somente quando o segmento do cliente é definido como all"
description: O patch MDVA-42969 corrige o problema em que a regra de produto relacionada só funciona quando o segmento do cliente é definido como todos. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13 está instalada. A ID do patch é MDVA-42969. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.
exl-id: 2877ba7a-2681-4de2-9c37-228de232424f
feature: Customer Service, Marketing Tools, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '481'
ht-degree: 0%

---

# MDVA-42969: A regra de produto relacionada só funciona quando o segmento do cliente é definido como all

O patch MDVA-42969 corrige o problema em que a regra de produto relacionada só funciona quando o segmento do cliente é definido como todos. Este patch está disponível quando a variável [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.13 está instalado. A ID do patch é MDVA-42969. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.1 - 2.4.2-p2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A regra de produto relacionada só funciona quando o segmento do cliente é definido como todos.

<u>Etapas a serem reproduzidas</u>:

1. Ir para **Lojas** > **Configuração** > **Catálogo** > **Relações de produto com base em regras** e defina **Mostrar produtos relacionados** = **Somente com base em regras**.
1. Ir para **Clientes** > **Segmentos** e criar um novo segmento: **Aplicar a** = **Visitantes e clientes registrados**.
1. Ir para **Marketing** > **Regras de produto relacionadas** e criar uma nova regra.

   ```code block
   Apply To = Related Products
   Customer Segments = All
   Products to Match = SKU = <select a SKU>
   Products to Display = SKU +is one of+ Constant Value (specify 1-3 products)
   ```

1. Abra o produto correspondente na vitrine e verifique se os Produtos a serem exibidos são mostrados.
1. Modifique a regra criada na etapa três e defina **Segmentos do cliente** = **Específico** > **Segmento** da etapa dois.
1. Abra o produto correspondente na loja.

<u>Resultados esperados</u>:

Os produtos relacionados com base em regras são exibidos na loja para visitantes no produto porque o segmento do cliente é criado com a seguinte configuração:

**Aplicar a** = **Visitantes e clientes registrados**

<u>Resultados reais</u>:

Nenhum produto relacionado é exibido.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de atualização de software > Aplicar patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatendimento de correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de patches de qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.
