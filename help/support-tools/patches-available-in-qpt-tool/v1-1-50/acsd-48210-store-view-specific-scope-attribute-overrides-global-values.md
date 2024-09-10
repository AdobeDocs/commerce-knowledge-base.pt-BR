---
title: "ACSD-48210: o atributo de escopo específico da exibição de armazenamento substitui os valores globais"
description: Aplique o patch ACSD-48210 para corrigir o problema do Adobe Commerce de atualizar um atributo *[!UICONTROL Website Scope]* em uma exibição de repositório específica que substitui os valores de atributo no escopo global.
feature: Products, Attributes
role: Admin, Developer
source-git-commit: 0fb14710d126aa4b4d6f5b6d0c70b190dcae81ae
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 0%

---

# ACSD-48210: os atributos específicos do escopo da exibição de armazenamento substituem os valores globais

O patch ACSD-48210 corrige o problema em que, ao atualizar um atributo *[!UICONTROL Website Scope]* em uma exibição de repositório específica, substitui os valores de atributo no escopo global. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.50 está instalado. A ID do patch é ACSD-48210. Observe que o problema foi corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Ao atualizar um atributo *[!UICONTROL Website Scope]* em uma exibição de repositório específica, os valores de atributo no escopo global são substituídos.

A importação de preços de produtos com várias linhas compartilhando o mesmo `SKU` e `store_view_code` causou atualizações incorretas nos preços nos escopos *[!UICONTROL All Store View]* e *[!UICONTROL Default Store]*. Modificar o atributo de escopo do site em uma exibição de armazenamento específica não substitui mais o valor do atributo no escopo global.
<u>Etapas a serem reproduzidas</u>:

1. Configure o *[!UICONTROL Catalog Price Scope]* para *[!UICONTROL Website]*.
1. Crie um produto simples chamado *SP01* e defina o preço como *$84,50*.
1. Importe o produto usando o seguinte CSV fornecido abaixo:

   ```
   sku,store_view_code,price
   SP01,default,99.99
   SP01,default,86.59
   ```

1. Verifique o preço do produto nos escopos *[!UICONTROL All Store View]* e *[!UICONTROL Default Store]*.

<u>Resultados esperados</u>:

* O primeiro valor não vazio é usado para o escopo *[!UICONTROL Default Store]*.
* O escopo *[!UICONTROL All Store View]* permanece inalterado.

<u>Resultados reais</u>:

* O preço de escopo *[!UICONTROL All Store View]* foi alterado para *$86,59*.
* O preço de escopo *[!UICONTROL Default Store]* foi alterado para *$86,59*.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] versão: uma nova ferramenta para autoatender patches de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando o [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
