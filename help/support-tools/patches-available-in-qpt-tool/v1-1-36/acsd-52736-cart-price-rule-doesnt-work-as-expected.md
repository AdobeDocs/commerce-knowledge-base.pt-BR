---
title: "ACSD-52736: [!UICONTROL Cart Price Rule] não funciona conforme o esperado"
description: Aplique o patch ACSD-52736 para corrigir o problema do Adobe Commerce em que um [!UICONTROL Cart Price Rule] que inclui os requisitos para a quantidade configurável do produto não funciona conforme esperado.
feature: Shopping Cart, Products
role: Admin, Developer
exl-id: 8403b418-b197-4695-88a8-e322b18cd4ad
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 0%

---

# ACSD-52736: [!UICONTROL Cart Price Rule] não funciona conforme o esperado

O patch ACSD-52736 corrige o problema em que um [!UICONTROL Cart Price Rule] que inclui os requisitos para a quantidade configurável do produto não funciona conforme esperado. Este patch está disponível quando a variável [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.36 está instalado. A ID do patch é ACSD-52736. Observe que o problema foi corrigido no Adobe Commerce 2.4.6.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.7 - 2.4.5-p4

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A [!UICONTROL Cart Price Rule] que inclui os requisitos para a quantidade configurável do produto não funciona como esperado.

<u>Etapas a serem reproduzidas</u>:

1. Criar uma regra de carrinho:
   * [!UICONTROL Apply] = Porcentagem do desconto de preço do produto
   * [!UICONTROL Discount Amount] = 60
   * [!UICONTROL Maximum Qty Discount is Applied to] = 1
   * [!UICONTROL Discount Qty Step (Buy X)] = 1
   * Aplique a regra somente aos itens do carrinho que correspondem às seguintes condições: A quantidade no carrinho é 1
2. Adicionar um produto com [!UICONTROL Qty] = 2, para o carrinho.
3. Verifique os preços do carrinho.

<u>Resultados esperados</u>:

A regra não é aplicada porque a quantidade de produtos no carrinho é *2*.

<u>Resultados reais</u>:

O desconto é aplicado.

<u> Etapas adicionais necessárias após a instalação do patch</u>:

Após aplicar o patch, as condições da regra do carrinho usando o *Quantidade* o atributo deve ser removido e adicionado novamente.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.
