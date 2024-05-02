---
title: "ACSD-54680: a Cotação B2B de um produto com Várias Fontes Atribuídas não pode ser processada"
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

O patch ACSD-54680 corrige o problema em que a Cotação B2B de um produto com Várias Fontes Atribuídas não pode ser processada. Este patch está disponível quando a variável [!DNL Quality Patches Tool (QPT)] O 1.1.40 está instalado. A ID do patch é ACSD-54680. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.0 - 2.4.5-p5

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A Cotação B2B de um produto com Várias Fontes Atribuídas não pode ser processada.

<u>Etapas a serem reproduzidas</u>:

1. Ir para **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Sources]** e criar duas novas fontes: **Origem 1** e **Origem 2**.
1. Ir para **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Stocks]** e criar um novo Stock: **Stock A**, atribua-o ao site principal e atribua **Origem 1** e **Origem 2** a ele.
1. Criar um produto simples, atribuir **Origem 1** e **Origem 2** e defina Qtd. = *2* para cada origem. (a quantidade comercializável do produto deve ser *4* como resultado).
1. Crie uma Conta de Empresa.
1. Vá para a **[!UICONTROL Storefront]** e faça logon na conta da empresa.
1. Adicionar o produto simples ao carrinho de compras com qtd. = *4*.
1. Abra o *[!UICONTROL Shopping cart]* e clique em **[!UICONTROL Request a quote]** botão.
1. Adicione um comentário e um nome de citação e clique em **[!UICONTROL Send a Request]** botão.
1. Ir para **[!UICONTROL Admin]** > **[!UICONTROL Sales]** > **[!UICONTROL Quotes]**.
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

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.
