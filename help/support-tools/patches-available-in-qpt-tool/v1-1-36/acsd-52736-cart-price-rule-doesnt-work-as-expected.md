---
title: "ACSD-52736: [!UICONTROL Cart Price Rule] não funciona como esperado"
description: Aplique o patch ACSD-52736 para corrigir o problema do Adobe Commerce em que um [!UICONTROL Cart Price Rule] que inclui os requisitos para a quantidade de produto configurável não funciona conforme esperado.
feature: Shopping Cart, Products
role: Admin, Developer
exl-id: 8403b418-b197-4695-88a8-e322b18cd4ad
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 0%

---

# ACSD-52736: [!UICONTROL Cart Price Rule] não funciona como esperado

O patch ACSD-52736 corrige o problema em que um [!UICONTROL Cart Price Rule] que inclui os requisitos para a quantidade de produto configurável não funciona como esperado. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.36 está instalado. A ID do patch é ACSD-52736. Observe que o problema foi corrigido no Adobe Commerce 2.4.6.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.7 - 2.4.5-p4

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Um [!UICONTROL Cart Price Rule] que inclui os requisitos para a quantidade de produto configurável não funciona como esperado.

<u>Etapas a serem reproduzidas</u>:

1. Criar uma regra de carrinho:
   * [!UICONTROL Apply] = Porcentagem de desconto no preço do produto
   * [!UICONTROL Discount Amount] = 60
   * [!UICONTROL Maximum Qty Discount is Applied to] = 1
   * [!UICONTROL Discount Qty Step (Buy X)] = 1
   * Aplique a regra somente aos itens do carrinho que correspondem às seguintes condições: A quantidade no carrinho é 1
2. Adicione um produto com [!UICONTROL Qty] = 2 ao carrinho.
3. Verifique os preços do carrinho.

<u>Resultados esperados</u>:

A regra não é aplicada porque a quantidade de produtos no carrinho é *2*.

<u>Resultados reais</u>:

O desconto é aplicado.

<u> Etapas adicionais necessárias após a instalação do patch</u>:

Após aplicar o patch, as condições da regra do carrinho que usam o atributo *Quantidade* devem ser removidas e adicionadas novamente.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] versão: uma nova ferramenta para autoatender patches de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando o [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
