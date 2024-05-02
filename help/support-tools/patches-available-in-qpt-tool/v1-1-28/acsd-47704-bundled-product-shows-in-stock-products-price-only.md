---
title: "ACSD-47704: o produto empacotado mostra o preço dos produtos em estoque somente"
description: Aplique o patch ACSD-47704 para corrigir o problema do Adobe Commerce em que um produto incluído mostra somente o preço dos produtos em estoque.
exl-id: 91fbeaf7-4bc2-49b1-a561-c3e63f193eaa
feature: Admin Workspace, Customer Service, Orders, Products
role: Admin
source-git-commit: 3eeb86c2644f8a04ddcf5e205bc400d2ca9969af
workflow-type: tm+mt
source-wordcount: '605'
ht-degree: 0%

---

# ACSD-47704: o produto empacotado mostra o preço dos produtos em estoque somente

O patch ACSD-47704 corrige o problema em que os preços de segmento do cliente são armazenados incorretamente em cache entre grupos de clientes. Este patch está disponível quando a variável [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.28 está instalado. A ID do patch é ACSD-47704. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.1-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O preço de um produto agrupado com o Dynamic Pricing ativado está incorreto porque apenas os itens em estoque estão incluídos.

<u>Etapas a serem reproduzidas</u>:

1. Acesse o painel Administrador do Commerce.
1. Ir para **[!UICONTROL CATALOG]** > **[!UICONTROL Products]** > **[!UICONTROL Add Product]** > **[!UICONTROL Bundle Product]**.
1. Definir **[UICONROL Dynamic Price]** para **[!UICONTROL Yes]**.
1. Itens do pacote:
   * Definir **[!UICONTROL Ship bundle items]** para **[!UICONTROL Together]**
   * Selecionar **[!UICONTROL Add Option]**
      * **[!UICONTROL Title]** = o1
      * **[!UICONTROL Input type]** = **[!UICONTROL Dropdown]**
      * Marcar caixa de seleção necessária
      * Adicione qualquer produto simples que esteja em estoque; por exemplo, Joust Duffle Bag SKU 24-MB01. Antes de adicionar o produto, observe o preço - US$ 34
   * Quantidade padrão: 1
   * Selecionar **[!UICONTROL Add Option]**
      * **[!UICONTROL Option Title]** = o2
      * **[!UICONTROL Input type]** = **[!UICONTROL Dropdown]**
      * Marcar caixa de seleção necessária
      * Adicione qualquer produto simples que esteja em estoque, diferente do produto adicionado na etapa anterior; por exemplo - Strive Shoulder Pack 24-MB04. Antes de adicionar o produto, observe o preço - US$ 32
      * Quantidade padrão: 1
1. Salvar produto.
1. Acesse a loja e localize o produto criado nas etapas anteriores. Observe seu preço - US$ 66 (66 = 32 + 34).
Atualmente, o preço do pacote de produtos é igual à soma dos preços de suas opções.
1. Acesse o painel Administrador do Commerce. Ir para **[!UICONTROL CATALOG]** > **[!UICONTROL Products]**.
1. Encontre um dos produtos simples atribuídos como opção ao produto incluído anteriormente: SKU 24-MB01 e um preço de US$ 34.
1. Altere sua quantidade para 0.
1. Salve o produto.
1. Acesse a loja e localize o produto do pacote criado nas etapas anteriores. Anote o preço - US$ 32. Anteriormente, o preço era de US$ 66, que era a soma de US$ 34 de SKU 24-MB01 e US$ 32 de SKU 24-MB04. Agora que o produto com 24 MB01 está esgotado, o preço do pacote está listado como US$ 32. É o preço do outro produto, que é uma opção em estoque.

<u>Resultados esperados</u>:

O preço de pacotes de produtos com Dynamic Pricing ativado é calculado de forma consistente, independentemente de as opções estarem em estoque ou esgotadas.

<u>Resultados reais</u>:

O preço do produto do pacote com o Dynamic Pricing habilitado foi calculado incorretamente. Leva em conta somente as opções que estão em estoque, resultando em uma quantidade menor exibida do que a real quando uma das opções está fora do estoque.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.
