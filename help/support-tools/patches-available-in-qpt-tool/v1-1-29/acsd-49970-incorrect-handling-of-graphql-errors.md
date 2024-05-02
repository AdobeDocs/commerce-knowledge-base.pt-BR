---
title: "ACSD-49970: tratamento incorreto de erros do GraphQL"
description: Aplique o patch ACSD-49970 para corrigir o problema do Adobe Commerce em que há manipulação incorreta de erros do GraphQL quando [!UICONTROL New Relic Reporting] está ativada.
exl-id: 70acade5-02a5-4769-86e2-5c566b2af709
feature: GraphQL, Observability
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---

# ACSD-49970: Tratamento incorreto de erros do GraphQL

O patch ACSD-49970 corrige o problema em que há manipulação incorreta de erros do GraphQL quando *[!UICONTROL New Relic Reporting]* está ativada. Este patch está disponível quando a variável [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.29 está instalado. A ID do patch é ACSD-49970. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5 - 2.4.6

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

`GraphQLOperationNames` A chave não é tratada corretamente se a variável `logDataHelper` contém ou não essa chave.

<u>Etapas a serem reproduzidas</u>:

1. Executar `bin/magento deploy:mode:set developer`.
1. Faça logon no Administrador.
1. Ativar **[!UICONTROL New Relic Integration]** de **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL New Relic Reporting]**
(Observação: mesmo que um erro seja exibido informando que a variável [!DNL New Relic] extensão não estiver disponível, a configuração será salva).
1. Executar este *GraphQL* mutação para `http://yourMagentoDomain/graphql` do *[!DNL Altair]* cliente ou qualquer outro cliente ou via cURL.

   ```GraphQL
   mutation {
       createEmptyCart
   }
   ```

   (Observação: defina o **[!UICONTROL Header]** para [!UICONTROL Content-Currency:CA] antes de executá-lo).

   ```cURL
   curl --location 'http://yourMagentoDomain/graphql' \--header 'Content-Currency: CA' \--header 'Content-Type: application/json' \--header 'Cookie: PHPSESSID=b5147f63fe5014ea523f262946; private_content_version=8d53dfda210a6e9bc46f4e4a01ffd6c5' \--data '{"query":"mutation {\r\n  createEmptyCart\r\n}","variables":{}}'
   ```

<u>Resultados esperados</u>:

Não há *Exceção 500* em logs, `GraphQLOperationNames` A chave está sendo manipulada corretamente.

<u>Resultados reais</u>:

Existe uma *Exceção 500* em logs, `GraphQLOperationNames` A chave não está sendo manipulada corretamente.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.
