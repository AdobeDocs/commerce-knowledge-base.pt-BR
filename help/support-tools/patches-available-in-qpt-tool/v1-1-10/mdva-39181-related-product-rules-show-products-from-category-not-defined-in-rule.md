---
title: 'MDVA-39181: Regras de produtos relacionados mostram produtos da categoria indefinida na regra'
description: O patch MDVA-39181 resolve o problema em que as regras de produto relacionadas mostram produtos de uma categoria não definida na regra. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10 está instalada. A ID do patch é MDVA-39181. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.
exl-id: b6364d1c-2480-483a-9a83-ac91feeb14b9
feature: Categories, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---

# MDVA-39181: Regras de produtos relacionados mostram produtos da categoria indefinida na regra

O patch MDVA-39181 resolve o problema em que as regras de produto relacionadas mostram produtos de uma categoria não definida na regra. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10 está instalada. A ID do patch é MDVA-39181. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

As regras de produtos relacionados mostram produtos de categorias não definidas na regra.

<u>Pré-requisitos</u>:

Instalar dados de amostra.

<u>Etapas a serem reproduzidas</u>:

1. Crie uma marca de atributo e adicione-a ao **Conjunto de atributos principais**.
1. Escolha **Josie**, **Augusta** e **Ingrid** jaquetas para adicionar ao Brand Kitty de **Women** > **Tops** > **Jackets category**.
1. Escolha as **jaquetas Beaumont**, **Hyperion** e **Kenobi** para adicionar ao Brand Kitty em **Men** > **Tops** > **Categoria Jacket**.
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
1. Atualize a ID de categoria de **Mulheres** > **Tops** > **Jaquetas** caso seja diferente disso.

<u>Resultados esperados</u>:

Somente os produtos da mesma marca e da mesma categoria secundária são mostrados em produtos relacionados.

<u>Resultados reais</u>:

Os produtos relacionados são mostrados da mesma marca, mas a partir de uma categoria principal aleatória.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) na documentação do desenvolvedor.
