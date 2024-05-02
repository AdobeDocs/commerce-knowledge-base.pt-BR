---
title: "ACSD-51846: erro interno como [!DNL REST API] os níveis de carga não são validados"
description: Aplique o patch ACSD-51846 para corrigir o problema do Adobe Commerce em que um "Erro Interno" ocorre como todos os níveis de [!DNL REST API] a carga útil não é validada.
feature: REST
role: Developer
exl-id: 17ce5cca-063d-439c-9390-f5e2bf5b696b
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---

# ACSD-51846: erro interno como [!DNL REST API] os níveis de carga não são validados

O patch ACSD-51846 corrige o problema em que um &quot;Erro Interno&quot; ocorre como todos os níveis de [!DNL REST API] a carga útil não é validada. Este patch está disponível quando a variável [!DNL Quality Patches Tool (QPT)] O 1.1.36 está instalado. A ID do patch é ACSD-51846. Observe que o problema foi corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3-p2 - 2.4.5-p4

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Ocorre um &quot;erro interno&quot;, uma vez que todos os níveis de [!DNL REST API] a carga útil não é validada.

<u>Etapas a serem reproduzidas</u>:

1. Adicione um produto ao carrinho do cliente.
1. Envie o [!DNL REST API] solicitação para `rest/V1/carts/mine/estimate-shipping-methods` usando um atributo incorreto &quot;_rua._&quot; com um ponto no final.

```
 {
    "address": {
         "street.": [
             "\uc11c\uc6b8 \uac15\ubd81\uad6c \ud55c\ucc9c\ub85c166\uae38 2 (-\uc11c\uc6b8 \uac15\ubd81\uad6c \uc218\uc720\ub3d9 269-36)"
         ],
         "city": "pune",
         "region": null,
         "country_id": "IN",
         "postcode": "411015",
         "customer_id": "2",
         "firstname": "test",
         "lastname": "test",
         "middlename": null,
         "prefix": null,
         "suffix": null,
         "vat_id": null,
         "company": null,
         "telephone": "00000000000",
         "fax": null,
         "custom_attributes": []
     }
 }
```

<u>Resultados esperados</u>:

O endpoint deve validar o parâmetro e retornar a variável `400 status code` com uma mensagem de erro específica. Exemplo:

```
report.CRITICAL: LogicException: Property "Street." does not have accessor method "getStreet." in class "Magento\Quote\Api\Data\AddressInterface". in vendor/magento/framework/Reflection/NameFinder.php:103
```

<u>Resultados reais</u>:

O ponto de extremidade não valida o parâmetro errado e retorna o `500 status code` erro.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.
