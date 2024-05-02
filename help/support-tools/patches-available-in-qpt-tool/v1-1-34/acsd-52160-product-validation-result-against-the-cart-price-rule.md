---
title: "ACSD-52160: resultado da validação do produto em relação à regra de preço do carrinho"
description: Aplique o patch ACSD-52160 para corrigir o problema do Adobe Commerce em que o resultado da validação do produto em relação à regra de preço do carrinho não é avaliado corretamente com base na condição da regra *[!UICONTROL If an item is FOUND/NOT FOUND in the cart with All/Any of these conditions true]*.
exl-id: a371c539-4440-4c84-baa4-774c32f66e41
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---

# ACSD-52160: o resultado da validação do produto em relação à regra de preço do carrinho não é avaliado corretamente

O patch ACSD-52160 corrige o problema em que o resultado da validação do produto em relação à regra de preço do carrinho não é avaliado corretamente com base na condição da regra *[!UICONTROL If an item is FOUND/NOT FOUND in the cart with All/Any of these conditions true]*. Este patch está disponível quando a variável [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.34 está instalado. A ID do patch é ACSD-52160. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.6-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O resultado da validação do produto em relação à regra de preço do carrinho não é avaliado corretamente com base na condição da regra *[!UICONTROL If an item is FOUND/NOT FOUND in the cart with All/Any of these conditions true]*.

<u>Etapas a serem reproduzidas</u>:

1. Crie dois produtos atribuídos a duas categorias diferentes.
1. Criar um **[!UICONTROL Cart Price Rule]** com condições como:

   * **SKU 1** no *[!UICONTROL FOUND]* parâmetro
   * **SKU 2** no *[!UICONTROL NOT FOUND]* parâmetro

1. Adicione ambos os produtos ao carrinho.
1. Aplique o código do cupom.

<u>Resultados esperados</u>

O código do cupom não é aplicado, pois o carrinho contém produtos da categoria restrita.

<u>Resultados reais</u>

O código do cupom é aplicado.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) no [!DNL Quality Patches Tool] guia.
