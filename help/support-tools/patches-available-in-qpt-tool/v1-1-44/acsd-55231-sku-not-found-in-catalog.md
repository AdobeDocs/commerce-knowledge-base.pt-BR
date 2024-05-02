---
title: "ACSD-55231: erro SKU não encontrado ao usar a funcionalidade de pedido rápido"
description: Aplique o patch ACSD-55231 para corrigir o problema do Adobe Commerce em que você obtém o erro *'O SKU não foi encontrado no catálogo'* ao tentar adicionar um produto ao carrinho usando a funcionalidade de pedido rápido.
feature: Products, Checkout, B2B
role: Admin, Developer
exl-id: 463c2c07-39ec-4b03-81f7-ec2f71f5af76
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '497'
ht-degree: 0%

---

# ACSD-55231: erro SKU não encontrado ao usar a funcionalidade de pedido rápido

O patch ACSD-55231 corrige o problema em que você obtém *&#39;O SKU não foi encontrado no catálogo&#39;* erro ao tentar adicionar um produto ao carrinho usando a funcionalidade de pedido rápido. Este patch está disponível quando a variável [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.44 está instalado. A ID do patch é ACSD-55231. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4-p3

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3 - 2.4.6-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Obtendo *&#39;o SKU não foi encontrado no catálogo&#39;* erro ao pesquisar produtos para adicionar ao carrinho usando a funcionalidade de pedido rápido.

<u>Etapas a serem reproduzidas</u>:

1. Instale o Adobe Commerce com módulos B2B.
1. Navegue até **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL B2B Features]** e defina:
   * **[!UICONTROL Enable company]**: *Sim*
   * **[!UICONTROL Enable Shared Catalog]**: *Sim*
   * **[!UICONTROL Enable Quick Order]**: *Sim*
1. Salve a configuração acima.
1. Ir para **[!UICONTROL Catalog]** > **[!UICONTROL Shared Catalogs]** e criar um novo catálogo compartilhado.
1. Navegue até **[!UICONTROL Customers]** > **[!UICONTROL All Customers]** e criar um novo cliente:
   * No campo de grupo, escolha o catálogo compartilhado criado recentemente e defina *[!UICONTROL Allow remote shopping assistance]* para *Sim*.
1. Gerar um produto simples com SKU *p12*, associá-lo à categoria *c1* e, em seguida, opte pelo catálogo compartilhado recém-criado na [!UICONTROL Product in Shared Catalog] seção.
1. Executar:

   ```
   bin/magento ind:rei 
   bin/magento c:f 
   bin/magento cron:run (multiple times)
   ```

1. Atualize a página de administração.
1. Navegue até **[!UICONTROL Customers]** > **[!UICONTROL All Customers]** e edite o cliente criado anteriormente.
1. Clique em **[!UICONTROL Login as customer]**.
1. Ir para **[!UICONTROL Quick order]**.
1. Pesquise o *p12* SKU e clique no link **[!UICONTROL Product Suggestion]**.
1. Adicione este produto ao carrinho e faça o pedido.
1. Retornar para **[!UICONTROL Quick Order]**, pesquisar por SKU *p12* novamente e clique em **[!UICONTROL Product Suggestion]**.

<u>Resultados esperados</u>:

Você pode adicionar o produto ao carrinho usando a funcionalidade de pedido rápido.

<u>Resultados reais</u>:

Não é possível adicionar o produto ao carrinho usando a funcionalidade de pedido rápido e obter *&#39;O SKU não foi encontrado no catálogo&#39;* erro ao pesquisar o SKU do produto.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.
