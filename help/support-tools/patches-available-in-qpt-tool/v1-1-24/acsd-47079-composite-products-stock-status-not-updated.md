---
title: "ACSD-47079: status de estoque dos produtos compostos não atualizado quando o status do estoque de subprodutos é alterado"
description: Aplique o patch ACSD-47079 para corrigir o problema do Adobe Commerce em que o status do estoque de produtos compostos (agrupados, agrupados e configuráveis) não é atualizado quando o status do estoque de subprodutos é alterado por meio do POST REST API /rest/V1/inventory/source-items.
exl-id: 603e4548-fb04-43b4-a033-4f2c7f665fae
feature: Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# ACSD-47079: status do estoque de produtos compostos não atualizado quando o status do estoque de subprodutos é alterado

O patch ACSD-47079 corrige o problema em que o status do estoque de produtos compostos (empacotados, agrupados e configuráveis) não é atualizado quando o status do estoque de subprodutos é alterado por meio do POST REST API `/rest/V1/inventory/source-items`. Este patch está disponível quando a variável [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.24 está instalado. A ID do patch é ACSD-47079. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.4-p2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O status do estoque de produtos compostos (pacote, agrupado e configurável) não é atualizado quando o status do estoque de subprodutos é alterado por meio do POST REST API `/rest/V1/inventory/source-items`.

<u>Etapas a serem reproduzidas</u>:

1. Crie um produto configurável, agrupado e agrupado com um produto filho simples para cada um.
1. Definir cada status de produto filho simples como **[!UICONTROL Out of Stock]** usando o `source-items` chamada à API.
1. Verifique agora o status do estoque do produto principal.

<u>Resultados esperados</u>:

O status do produto principal é [!UICONTROL Out of Stock].

<u>Resultados reais</u>:

O status do produto principal é [!UICONTROL In Stock].

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.
