---
title: "ACSD-48366: imagem do produto não exibida no modelo de email do [!UICONTROL Back to Stock]"
description: Aplique o patch ACSD-48366 para corrigir o problema do Adobe Commerce em que a imagem em miniatura do produto não é exibida no email de alerta de estoque do produto.
exl-id: 57b549b0-6e97-4d5f-927e-9585f3257872
feature: Admin Workspace, Communications, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# ACSD-48366: imagem do produto não exibida no modelo de email [!UICONTROL Back to Stock]

O patch ACSD-48366 corrige o problema em que a imagem em miniatura do produto não é exibida no email de alerta de estoque do produto. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.26 está instalado. A ID do patch é ACSD-48366. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.6

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A imagem do produto não é exibida no modelo de email [!UICONTROL Back to Stock].

<u>Etapas a serem reproduzidas</u>:

1. Habilite *[!UICONTROL Product Alert]* para *[!UICONTROL Back in Stock]* indo para **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Product Alert]** > **[!UICONTROL Allow Alert When Product Comes Back in Stock]** = *[!UICONTROL Yes]*.
1. Habilite *[!UICONTROL Display Out of Stock Products]* indo até **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Display Out of Stock]** = *[!UICONTROL Yes]*.
1. Crie um produto simples com quantidade = 0.
1. Crie um cliente na loja e assine o produto acima para receber alertas de produtos quando estiver em estoque.
1. Faça o produto em estoque.
1. Executar o cron de alerta do produto.

   ```
   n98-magerun2.phar sys:cron:run catalog_product_alert
   ```

1. Iniciar o alerta do produto para o cliente.

   ```
   bin/magento queue:consumers:start product_alert
   ```

1. Verifique o email. O email de alerta de estoque agora deve estar disponível na captura de email.

<u>Resultados esperados</u>:

A imagem do produto é exibida no email de alerta de estoque.

<u>Resultados reais</u>:

A imagem do produto não está disponível no email de alerta de estoque.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] versão: uma nova ferramenta para autoatender patches de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando o [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
