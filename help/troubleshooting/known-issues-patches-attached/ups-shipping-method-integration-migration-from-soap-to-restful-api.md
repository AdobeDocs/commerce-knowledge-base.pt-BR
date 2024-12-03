---
title: Migração da integração do método de envio [!DNL UPS] de [!DNL SOAP] para [!DNL RESTful API]
promoted: true
description: Aplique um patch para lidar com a  [!DNL UPS] migração de integração de método de envio de  [!DNL SOAP] para [!DNL RESTful API] para Adobe Commerce 2.4.4 - 2.4.6-pX.
feature: Shipping/Delivery
role: Developer
exl-id: 8ab5d4a8-0155-4b2c-ab67-d0bd2f949a07
source-git-commit: 6694bb1e041e6285f5bd5a05a1c37b7062521f52
workflow-type: tm+mt
source-wordcount: '640'
ht-degree: 0%

---

# Migração da integração do método de envio [!DNL UPS] de [!DNL SOAP] para [!DNL RESTful API]

>[!NOTE]
>
>Se você carregou algum dos três patches deste artigo antes de **6 de junho de 2024**: se estiver com este problema por causa das [!DNL Metric System/SI] medidas (quilogramas e centímetros) não estarem sendo usadas, reaplique um desses novos patches atualizados agora publicados neste artigo para a sua versão 2.4.4+/2.4.5+/2.4.6+ do Adobe Commerce/Magento Open Source mais uma vez, caso contrário, não será possível selecionar as [!DNL Metric System/SI] medidas de **quilogramas** e **centímetros** no 8} métodos de envio no **[!DNL Admin configuration]**. [!DNL UPS] Esses novos patches são compatíveis com os patches lançados anteriormente. Este problema será corrigido permanentemente no escopo da próxima versão 2.4.7-p1 do Adobe Commerce planejada para **11 de junho de 2024**.

>[!NOTE]
>
>Se você carregou algum dos três patches deste artigo antes de **10 de outubro de 2023**, reaplique um desses patches agora publicados neste artigo para sua versão 2.4.4+/2.4.5+/2.4.6+ do Adobe Commerce/Magento Open Source mais uma vez, caso contrário, você não poderá selecionar e configurar métodos de envio específicos do [!DNL UPS] no **[!DNL Admin configuration]** e terá que habilitar todos eles. Esses novos patches são compatíveis com os patches lançados anteriormente.

Este artigo fornece uma correção para resolver problemas com a migração da integração do método de envio [!DNL United Parcel Service (UPS)] do [!DNL SOAP] para o [!DNL RESTful API] para Adobe Commerce 2.4.4 - 2.4.6-pX.

De acordo com as últimas atualizações do Modelo de Segurança do [!DNL UPS API], o [!DNL UPS] implementou um modelo de segurança do [!DNL OAuth 2.0] para todos os [!DNL APIs] (Mais detalhes disponíveis no [[!DNL UPS] Guia de Migração da Chave de Acesso ao Portal do Desenvolvedor](https://developer.ups.com/oauth-developer-guide?loc=en_US&amp;sp_rid=NTA5MzQ1OTE2NjEyS0&amp;sp_mid=72989914)) para aprimorar a segurança geral e reduzir fraudes e fornecer recursos [!DNL API] aprimorados.

Essa alteração afeta nossa implementação de integração do método de envio [!DNL UPS] atual no Adobe Commerce e requer que corrijamos nossa implementação atual e migremos de [!DNL SOAP API] para [!DNL RESTful API] para dar suporte aos protocolos de autenticação [!DNL OAuth 2.0].

**A partir de junho de 2024**, os comerciantes do Adobe Commerce não poderão fazer transações com nossa integração atual do [!DNL UPS]. Portanto, estamos lançando este hotfix, que permite que os comerciantes do Adobe Commerce 2.4.4+/2.4.5+/2.4.6+ migrem para o [!DNL UPS REST APIs] mais recente.

Esse problema será corrigido no Adobe Commerce/Magento Open Source versão 2.4.7 e a correção também será incluída na versão 2.4.7-beta2 em outubro de 2023.

## Produtos e versões afetados

Adobe Commerce na infraestrutura em nuvem e no local, e Magento Open Source:

* 2.4.4
* 2,4,4-pX
* 2.4.5
* 2,4,5-pX
* 2.4.6
* 2,4,6-pX

## Causas

O [!DNL UPS] lançou uma atualização de segurança [ para o  [!DNL API]](https://developer.ups.com/oauth-developer-guide?loc=en_US&amp;sp_rid=NTA5MzQ1OTE2NjEyS0&amp;sp_mid=72989914).

Se você tiver a União Europeia (outras origens podem enfrentar o mesmo problema) como Origem da Remessa, isso causará um erro na solicitação [!DNL UPS REST]:
&quot;*Uma remessa não pode ter KGS/IN, LBS/CM ou OZS/CM como sua unidade de medida.*&quot;

## Solução

Use os seguintes patches anexados, dependendo da sua versão do Adobe Commerce/Magento Open Source:

Para resolver o problema nas versões 2.4.4+, 2.4.5+ e 2.4.6+, você deve aplicar o patch correspondente à versão do Adobe Commerce/Magento Open Source abaixo.

## Correção

Use os seguintes patches anexados, dependendo da sua versão do Adobe Commerce/Magento Open Source:

### Para as versões 2.4.4, 2.4.4-pX:

* [AC-11984_UPS_Shipping_Method_Migration_REST_API_2.4.4x_COMPOSER.patch.zip](assets/AC-11984_UPS_Shipping_Method_Migration_REST_API_2.4.4x_COMPOSER.patch.zip)

### Para as versões 2.4.5, 2.4.5-pX:

* [AC-11983_UPS_Shipping_Method_Migration_REST_API_2.4.5x_COMPOSER.patch.zip](assets/AC-11983_UPS_Shipping_Method_Migration_REST_API_2.4.5x_COMPOSER.patch.zip)

### Para as versões 2.4.6, 2.4.6-pX:

* [AC-11916_UPS_Shipping_Method_Migration_REST_API_2.4.6x_COMPOSER.patch.zip](assets/AC-11916_UPS_Shipping_Method_Migration_REST_API_2.4.6x_COMPOSER.patch.zip)

## Como aplicar o patch

Descompacte o arquivo e consulte [Como aplicar um patch de compositor fornecido pelo Adobe](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento.html) em nossa base de dados de suporte para obter instruções.

## Como saber se os patches foram aplicados

Considerando que não é possível verificar facilmente se o problema foi corrigido, talvez você queira verificar se o patch foi aplicado com sucesso. Isso usa (Exemplo: *AC-9363*) como o patch a ser verificado.

<u>Você pode fazer isso executando as seguintes etapas</u>:

1. [Instalar o [!DNL Quality Patches Tool]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html).
1. Execute o comando:

   ```bash
   vendor/bin/magento-patches -n status |grep "9363|Status"
   ```

1. Você deve ver uma saída semelhante a esta, onde AC-9363 retorna o status *Aplicado*:

   ```bash
   ║ Id            │ Title                                                        │ Category        │ Origin                 │ Status      │ Details                                          ║ ║ N/A           │ ../m2-hotfixes/AC-9363_USPS_Ground_Advantage_shipping_method_COMPOSER_patch.patch      │ Other           │ Local                  │ Applied     │ Patch type: Custom                                
   ```
