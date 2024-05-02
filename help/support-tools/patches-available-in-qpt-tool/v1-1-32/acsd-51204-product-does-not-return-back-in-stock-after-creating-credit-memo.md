---
title: "ACSD-51204: o produto não retorna ao estoque após criar o memorando de crédito"
description: Aplique o patch ACSD-51204 para corrigir o problema do Adobe Commerce em que o produto não retorna ao estoque após criar o memorando de crédito.
feature: Orders, Products, Returns
role: Admin
exl-id: 302033bc-2ca5-40d6-b692-24ae46b21c31
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '401'
ht-degree: 0%

---

# ACSD-51204: o produto não retorna ao estoque após criar o memorando de crédito

O patch ACSD-51204 corrige o problema em que o produto não retorna ao estoque após criar o memorando de crédito. Este patch está disponível quando a variável [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.32 está instalado. A ID do patch é ACSD-51204. Observe que o problema foi corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3 - 2.4.6-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O produto esgotado não retorna em estoque após a criação do memorando de crédito.

<u>Etapas a serem reproduzidas</u>:

1. Instalar **[!UICONTROL Adobe Commerce]** e habilite o **[!UICONTROL Inventory Management Module]** com padrão *origem* e *estoque* somente.
1. Adicionar um **[!UICONTROL new product]** com uma quantidade de *10*.
1. Atribua o produto à **[!UICONTROL default stock]**.
1. Na Loja, adicione o produto ao carrinho e faça o pedido de uma quantidade total disponível de 10.
1. No painel de administração, gere uma *fatura* e *remessa* para o pedido.
1. Criar um **[!UICONTROL Credit Memo]** com o *retornar ao estoque* caixa de seleção marcada para todos os itens.
1. Verifique o nome do produto **[!UICONTROL Salable Quantity]** em Admin.

<u>Resultados esperados</u>:

A quantidade comercializável do produto deve retornar para *10*.

<u>Resultados reais</u>:

A quantidade vendável do produto é deixada como *0*.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) no [!DNL Quality Patches Tool] guia.
