---
title: "ACSD-47937: notificações de queda de preço não enviadas devido ao cache no nível do aplicativo"
description: Aplique o patch ACSD-47937 para corrigir o problema do Adobe Commerce em que as notificações de queda de preço nem sempre são enviadas devido ao armazenamento em cache no nível do aplicativo.
exl-id: f39c9ef6-4689-427f-bd61-3a52dec88be2
feature: Admin Workspace, Cache, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 0%

---

# ACSD-47937: notificações de queda de preço não enviadas devido ao armazenamento em cache no nível do aplicativo

O patch ACSD-47937 corrige o problema em que as notificações de queda de preço nem sempre são enviadas devido ao armazenamento em cache no nível do aplicativo. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.26 está instalado. A ID do patch é ACSD-47937. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 e 2.4.5-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4, 2.4.5 e 2.4.5-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os clientes não estão recebendo email de queda de preço de produto para alterações subsequentes de preço de produto.

<u>Etapas a serem reproduzidas</u>:

1. Habilitar **[!UICONTROL Product Alert]** para *[!UICONTROL Price Changes]* e *[!UICONTROL Back in Stock]* em **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Product Alert]**.
1. Habilitar **[!UICONTROL Display Out of Stock Products]**.
1. Crie um produto simples (ABC) com quantidade = 0.
1. Crie um cliente na loja e assine o produto acima para receber alertas de produtos em caso de queda de preços.
1. Iniciar o alerta de produto para clientes.

   ```PHP
   bin/magento queue:consumers:start product_alert
   ```

1. Baixe o preço do produto ABC.
1. Acione o cron de alerta do produto.

   ```PHP
   php n98-magerun2.phar sys:cron:run catalog_product_alert
   ```

1. Baixe o preço do produto ABC novamente.
1. Acione o cron de alerta do produto.

   ```PHP
   php n98-magerun2.phar sys:cron:run catalog_product_alert
   ```

>[!NOTE]
>
>Se você não estiver familiarizado com a ferramenta [!DNL n98], poderá executar `bin/magento cron:run command` como de costume e monitorar a tabela `cron_schedule` para verificar se o trabalho `catalog_product_alert` obterá status de sucesso.

<u>Resultados esperados</u>:

O segundo e-mail de queda de preço é enviado.

<u>Resultados reais</u>:

O e-mail da segunda redução de preço não é enviado.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] versão: uma nova ferramenta para autoatender patches de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando o [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
