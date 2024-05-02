---
title: "MDVA-39181: as regras de produto relacionadas mostram produtos da categoria não definidos na regra"
description: O patch MDVA-39181 resolve o problema em que as regras de produto relacionadas mostram produtos de uma categoria não definida na regra. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10 está instalada. A ID do patch é MDVA-39181. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.
exl-id: b6364d1c-2480-483a-9a83-ac91feeb14b9
feature: Categories, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---

# MDVA-39181: Regras de produtos relacionados mostram produtos da categoria indefinida na regra

O patch MDVA-39181 resolve o problema em que as regras de produto relacionadas mostram produtos de uma categoria não definida na regra. Este patch está disponível quando a variável [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.10 está instalado. A ID do patch é MDVA-39181. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

As regras de produtos relacionados mostram produtos de categorias não definidas na regra.

<u>Pré-requisitos</u>:

Instalar dados de amostra.

<u>Etapas a serem reproduzidas</u>:

1. Crie uma marca de atributo e adicione-a à **Conjunto de Atributos Superior**.
1. Escolher **Josie**, **Augusta**, e **Ingrid** jaquetas para adicionar ao Brand Kitty de **Mulheres** > **Topos** > **Categoria Casacos**.
1. Escolher **Beaumont**, **Hyperion**, e **Kenobi** jaquetas para adicionar ao Brand Kitty de **Homens** > **Topos** > **Categoria de jaqueta**.
1. Criar um produto relacionado com:

   ```markdown
   Apply To: Related Products
   Customer Segments: All
   ```

   * Produtos correspondentes:

   ```markdown
   If ALL of these conditions are TRUE
     Category is {}
     Brand is {}
   ```

   * Produtos a exibir:

   ```markdown
   If ALL of these conditions are TRUE
      Product Category is the same as Matched Product Category
      Product brand is Matched Product Brand
   ```

1. Abra o SKU WJ04 no front-end e verifique os produtos relacionados.
1. Atualizar a ID da categoria de **Mulheres** > **Topos** > **Jaquetas** caso seja diferente disso.

<u>Resultados esperados</u>:

Somente os produtos da mesma marca e da mesma categoria secundária são mostrados em produtos relacionados.

<u>Resultados reais</u>:

Os produtos relacionados são mostrados da mesma marca, mas a partir de uma categoria principal aleatória.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de atualização de software > Aplicar patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatendimento de correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de patches de qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.
