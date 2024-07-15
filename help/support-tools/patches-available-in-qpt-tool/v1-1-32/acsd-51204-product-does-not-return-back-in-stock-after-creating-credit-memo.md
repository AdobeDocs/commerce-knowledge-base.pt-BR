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

O patch ACSD-51204 corrige o problema em que o produto não retorna ao estoque após criar o memorando de crédito. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.32 está instalado. A ID do patch é ACSD-51204. Observe que o problema foi corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3 - 2.4.6-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O produto esgotado não retorna em estoque após a criação do memorando de crédito.

<u>Etapas a serem reproduzidas</u>:

1. Instale o **[!UICONTROL Adobe Commerce]** e habilite o **[!UICONTROL Inventory Management Module]** somente com a *origem* e o *estoque* padrão.
1. Adicione um **[!UICONTROL new product]** com uma quantidade de *10*.
1. Atribua o produto a **[!UICONTROL default stock]**.
1. Na Loja, adicione o produto ao carrinho e faça o pedido de uma quantidade total disponível de 10.
1. No painel de administração, gere uma *fatura* e uma *remessa* para o pedido.
1. Crie um **[!UICONTROL Credit Memo]** com a caixa de seleção *retornar ao estoque* marcada para todos os itens.
1. Verifique o **[!UICONTROL Salable Quantity]** do produto no Administrador.

<u>Resultados esperados</u>:

A quantidade comercializável do produto deve retornar para *10*.

<u>Resultados reais</u>:

A quantidade vendável do produto é deixada como *0*.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] versão: uma nova ferramenta para autoatender patches de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando o [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) no guia [!DNL Quality Patches Tool].
