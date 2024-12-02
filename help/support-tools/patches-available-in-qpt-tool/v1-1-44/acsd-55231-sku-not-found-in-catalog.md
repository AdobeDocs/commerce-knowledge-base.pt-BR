---
title: 'ACSD-55231: erro SKU não encontrado ao usar a funcionalidade de pedido rápido'
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

O patch ACSD-55231 corrige o problema em que você obtém o erro *&#39;A SKU não foi encontrada no catálogo&#39;* ao tentar adicionar um produto ao carrinho usando a funcionalidade de pedido rápido. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.44 está instalado. A ID do patch é ACSD-55231. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4-p3

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3 - 2.4.6-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Erro ao obter *&#39;a SKU não encontrada no catálogo&#39;* ao pesquisar produtos para adicionar ao carrinho usando a funcionalidade de pedido rápido.

<u>Etapas a serem reproduzidas</u>:

1. Instale o Adobe Commerce com módulos B2B.
1. Navegue até **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL B2B Features]** e defina:
   * **[!UICONTROL Enable company]**: *Sim*
   * **[!UICONTROL Enable Shared Catalog]**: *Sim*
   * **[!UICONTROL Enable Quick Order]**: *Sim*
1. Salve a configuração acima.
1. Vá para **[!UICONTROL Catalog]** > **[!UICONTROL Shared Catalogs]** e crie um novo catálogo compartilhado.
1. Navegue até **[!UICONTROL Customers]** > **[!UICONTROL All Customers]** e crie um novo cliente:
   * No campo de grupo, escolha o catálogo compartilhado criado recentemente e defina *[!UICONTROL Allow remote shopping assistance]* como *Sim*.
1. Gere um produto simples com SKU *p12*, associe-o à categoria *c1* e opte pelo catálogo compartilhado recém-criado na seção [!UICONTROL Product in Shared Catalog].
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
1. Pesquise o SKU *p12* e clique no **[!UICONTROL Product Suggestion]**.
1. Adicione este produto ao carrinho e faça o pedido.
1. Retorne a **[!UICONTROL Quick Order]**, procure por SKU *p12* novamente e clique em **[!UICONTROL Product Suggestion]**.

<u>Resultados esperados</u>:

Você pode adicionar o produto ao carrinho usando a funcionalidade de pedido rápido.

<u>Resultados reais</u>:

Você não pode adicionar o produto ao carrinho usando a funcionalidade de pedido rápido e obter o erro *&#39;A SKU não foi encontrada no catálogo&#39;* ao pesquisar a SKU do produto.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] versão: uma nova ferramenta para autoatender patches de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando o [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
