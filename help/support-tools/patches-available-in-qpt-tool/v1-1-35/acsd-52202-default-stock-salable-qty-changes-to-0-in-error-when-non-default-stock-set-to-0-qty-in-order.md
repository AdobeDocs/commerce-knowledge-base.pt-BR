---
title: 'ACSD-52202: A quantidade padrão de estoque comercializável muda para 0 com erro quando o estoque não padrão é definido como 0 qtd. na ordem'
description: Aplique o patch ACSD-52202 para corrigir o problema do Adobe Commerce em que uma quantidade padrão vendável de estoque é alterada para 0 com erro quando a quantidade sem estoque padrão é definida como 0 em um pedido.
feature: Inventory, Products
role: Admin
exl-id: 8a3b5da4-cf16-41c8-b2d5-b740d638c745
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---

# ACSD-52202: A quantidade padrão de estoque disponível muda para 0 com erro quando o estoque não padrão é definido como 0 na quantidade de uma ordem

O patch ACSD-52202 corrige o problema em que uma quantidade à venda (qtd.) de estoque padrão é alterada para 0 com erro quando o estoque não padrão é definido como 0 na quantidade de um pedido. Este patch está disponível quando o [!DNL Quality Patches Tool (QPT)] 1.1.35 está instalado. A ID do patch é ACSD-52202. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3 - 2.4.6-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A quantidade padrão de estoque disponível muda para 0 com erro quando o estoque não padrão é definido como 0 na quantidade de um pedido.

<u>Etapas a serem reproduzidas</u>:

1. Faça logon no [!DNL Admin].
1. Criar **site2**.
1. Criar **origem2** personalizada.
1. Criar **stock2** personalizado.
1. Atribua a **origem2** e o **estoque2** ao **site1** e a origem e o estoque padrão ao site padrão.
1. Crie um produto simples e atribua **qty** = *10* para a origem padrão e **qty** = *1* para a origem **source2**.
1. Fazer um pedido com **qty** = *1* para **site2**.
1. Criar uma fatura e uma remessa.
1. Verifique a **quantidade comercializável** do produto simples.

<u>Resultados esperados</u>:

A **quantidade vendável** = *10* para **origem2**.

<u>Resultados reais</u>:

A **quantidade vendável** = *0* para ambas as fontes.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] versão: uma nova ferramenta para autoatender patches de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando o [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
