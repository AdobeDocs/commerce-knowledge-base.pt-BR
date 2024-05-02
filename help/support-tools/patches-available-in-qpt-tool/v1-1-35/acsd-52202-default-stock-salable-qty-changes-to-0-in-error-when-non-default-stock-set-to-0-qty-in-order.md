---
title: "ACSD-52202: A quantidade padrão de estoque comercializável muda para 0 com erro quando o estoque não padrão é definido como 0 qtd. na ordem"
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

O patch ACSD-52202 corrige o problema em que uma quantidade à venda (qtd.) de estoque padrão é alterada para 0 com erro quando o estoque não padrão é definido como 0 na quantidade de um pedido. Este patch está disponível quando a variável [!DNL Quality Patches Tool (QPT)] O 1.1.35 está instalado. A ID do patch é ACSD-52202. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3 - 2.4.6-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A quantidade padrão de estoque disponível muda para 0 com erro quando o estoque não padrão é definido como 0 na quantidade de um pedido.

<u>Etapas a serem reproduzidas</u>:

1. Faça logon no [!DNL Admin].
1. Criar **site2**.
1. Criar personalizado **source2**.
1. Criar personalizado **stock2**.
1. Atribua a **source2** e **stock2** para **site1** e a fonte e o estoque padrão para o site padrão.
1. Criar um produto simples e atribuir **qtd** = *10* para origem padrão e **qtd** = *1* para o **source2** origem.
1. Fazer um pedido com **qtd** = *1* para **site2**.
1. Criar uma fatura e uma remessa.
1. Verifique o produto simples **quantidade comercializável**.

<u>Resultados esperados</u>:

A variável **quantidade comercializável** = *10* para **source2**.

<u>Resultados reais</u>:

A variável **quantidade comercializável** = *0* para ambas as fontes.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.
