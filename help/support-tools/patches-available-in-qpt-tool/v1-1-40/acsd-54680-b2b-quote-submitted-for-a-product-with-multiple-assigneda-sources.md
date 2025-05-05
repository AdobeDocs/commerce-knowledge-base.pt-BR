---
title: 'ACSD-54680: a Cotação B2B de um produto com Várias Fontes Atribuídas não pode ser processada'
description: Aplique o patch ACSD-54680 para corrigir o problema do Adobe Commerce em que a Cotação B2B de um produto com Várias Fontes Atribuídas não pode ser processada.
feature: B2B
role: Admin, Developer
exl-id: 4d05714c-d32d-46f3-b857-81704c9e96cd
source-git-commit: f12e25ac5dd607cc614dd99c90c5e104b2cee6a8
workflow-type: tm+mt
source-wordcount: '444'
ht-degree: 0%

---

# ACSD-54680: a Cotação B2B de um produto com Várias Fontes Atribuídas não pode ser processada.

O patch ACSD-54680 corrige o problema em que a Cotação B2B de um produto com Várias Fontes Atribuídas não pode ser processada. Este patch está disponível quando o [!DNL Quality Patches Tool (QPT)] 1.1.40 está instalado. A ID do patch é ACSD-54680. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.0 - 2.4.5-p5

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A Cotação B2B de um produto com Várias Fontes Atribuídas não pode ser processada.

<u>Etapas a serem reproduzidas</u>:

1. Vá para **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Sources]** e crie duas novas fontes: **Source 1** e **Source 2**.
1. Vá para **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Stocks]** e crie um novo Stock: **Stock A**, atribua-o ao site principal e atribua a ele o **Source 1** e o **Source 2**.
1. Crie um produto Simples, atribua o **Source 1** e o **Source 2** e defina a Quantidade = *2* para cada origem. (a quantidade vendável do produto deve ser *4* como resultado).
1. Crie uma Conta de Empresa.
1. Vá para **[!UICONTROL Storefront]** e faça logon na conta da empresa.
1. Adicionar o produto simples ao carrinho de compras com quantidade = *4*.
1. Abra o *[!UICONTROL Shopping cart]* e clique no botão **[!UICONTROL Request a quote]**.
1. Adicione um comentário e um nome de citação e clique no botão **[!UICONTROL Send a Request]**.
1. Vá para **[!UICONTROL Admin]** > **[!UICONTROL Sales]** > **[!UICONTROL Quotes]**.
1. Abrir cotação enviada recentemente.

<u>Resultados esperados</u>:

Os itens cotados contêm o produto solicitado.

<u>Resultados reais</u>:

A seção da página de itens entre aspas está vazia e não é possível processar a cotação.
`var/log/system.log` contém

```
report.CRITICAL: TypeError: number_format() expects parameter 1 to be float, null given in .../vendor/magento/module-negotiable-quote/Model/QuoteUpdatesInfo.php:232
```

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] versão: uma nova ferramenta para autoatender patches de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando o [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
