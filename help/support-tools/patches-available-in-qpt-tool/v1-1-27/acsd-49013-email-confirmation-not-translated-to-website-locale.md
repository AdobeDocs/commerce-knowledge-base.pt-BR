---
title: "ACSD-49013: confirmação de email não traduzida para o local do site"
description: Aplique o patch ACSD-49013 para corrigir o problema do Adobe Commerce, em que a confirmação por email não é traduzida para o local do site ao criar clientes usando a API em massa.
exl-id: 68203bd4-021a-4736-a793-4b6663a9c66b
feature: Admin Workspace, Communications
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 0%

---

# ACSD-49013: confirmação de email não traduzida para o local do site

O patch ACSD-49013 corrige o problema em que a confirmação de email não é traduzida para o local do site ao criar clientes usando a API em massa. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.27 está instalado. A ID do patch é ACSD-49013. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3 - 2.4.6

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A confirmação por email não é traduzida para o local do site ao criar clientes usando a API em massa.

<u>Etapas a serem reproduzidas</u>:

1. Instalar uma localidade diferente como `de_DE`.
1. Configurar *RabbitMQ*.
1. Execute `bin/magento setup:upgrade` para instalar as filas no RabbitMQ e configurar o pacote de idiomas.
1. Criar um site adicional em [!UICONTROL Admin] > **[!UICONTROL Stores]** > **[!UICONTROL All Stores]**.
1. Defina a localidade deste novo site como `de_DE` em [!UICONTROL Admin] > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL Locale Options]**.
1. Execute uma chamada de API para criar uma conta de cliente usando a API em massa. Use o `website_id` correspondente.

   `Endpoint: /rest/async/bulk/V1/customers`

   ```
   [{
       "customer": {
       "email": "test@example.com",
       "firstname": "test",
       "lastname": "test",
       "website_id": 2
       },
       "password": "Passw0rd!"
   }]
   ```

1. Executar `bin/magento queue:consumers:start async.operations.all --single-thread --max-messages=10`.
1. Você pode ver que a conta do cliente foi criada corretamente no site especificado.
1. Verifique o email recebido para registro do cliente.

<u>Resultados esperados</u>:

Como o cliente é criado em um site especificado, o email de registro é enviado usando a localidade desse site.

<u>Resultados reais</u>:

O cliente é criado corretamente no site especificado, mas o email de registro é enviado usando a localidade padrão quando a API em massa é usada.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] versão: uma nova ferramenta para autoatender patches de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando o [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
