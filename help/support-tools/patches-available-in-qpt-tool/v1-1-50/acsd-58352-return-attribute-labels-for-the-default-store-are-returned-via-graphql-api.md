---
title: 'ACSD-58352: Os rótulos de atributo de retorno para o armazenamento padrão são retornados por meio da API  [!DNL GraphQL] '
description: Aplique o patch ACSD-58352 para corrigir o problema do Adobe Commerce em que os rótulos de atributo de retorno para o armazenamento padrão são retornados por meio da API  [!DNL GraphQL]  quando uma exibição de armazenamento não padrão é especificada no cabeçalho da solicitação.
feature: GraphQL, Returns
role: Admin, Developer
exl-id: 372a50bb-28e1-4259-97d1-011956b73d59
source-git-commit: a84c3d296deb49d419be78f454696177a974d923
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 0%

---

# ACSD-58352: Rótulos de atributos de retorno para o armazenamento padrão são retornados pela API [!DNL GraphQL]

O patch ACSD-58352 corrige o problema em que os rótulos de atributo de retorno para o armazenamento padrão são retornados por meio da API [!DNL GraphQL] quando uma exibição de armazenamento não padrão é especificada no cabeçalho da solicitação. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.50 está instalado. A ID do patch é ACSD-58352. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os rótulos de atributo de retorno para o armazenamento padrão são retornados pela API [!DNL GraphQL].

<u>Etapas a serem reproduzidas</u>:

1. Habilite o **[!UICONTROL Return Merchandising Authorization]**.
1. Crie um *[!UICONTROL Additional Store]* e um *[!UICONTROL Store View]* no site padrão.
1. Edite o atributo de retorno **[!UICONTROL Reason for Return]** e adicione rótulos para todas as exibições de loja.
1. Criar um *[!UICONTROL Order]*.
1. Crie um *[!UICONTROL Return]* para esse pedido. Verifique se *[!UICONTROL Return]* está no status *[!UICONTROL Pending]*.
1. Enviar uma consulta de Cliente [!DNL GraphQL] com o [!UICONTROL Store View] não padrão especificado no cabeçalho:

   ```
   query {
       customer {
           returns {
               items {
                   items {
                       custom_attributes {
                           label
                           value
                       }
                   }
               }
           }
       }
   }
   ```

1. Observe a resposta.

<u>Resultados esperados</u>

Os rótulos de retorno na resposta [!DNL GraphQL] são para o [!UICONTROL Store View] definido no cabeçalho da solicitação.

<u>Resultados reais</u>:

Os rótulos de retorno na resposta [!DNL GraphQL] são para o padrão [!UICONTROL Store View].

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] versão: uma nova ferramenta para autoatender patches de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando o [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
