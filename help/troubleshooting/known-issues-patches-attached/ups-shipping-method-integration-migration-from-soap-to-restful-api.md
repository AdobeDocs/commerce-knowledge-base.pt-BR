---
title: '[!DNL UPS] migração da integração do método de envio do [!DNL SOAP] para [!DNL RESTful API]'
promoted: true
description: Aplique uma correção para lidar com a [!DNL UPS] migração da integração do método de envio do [!DNL SOAP] para [!DNL RESTful API] para Adobe Commerce 2.4.4 - 2.4.6-pX.
feature: Shipping/Delivery
role: Developer
exl-id: 8ab5d4a8-0155-4b2c-ab67-d0bd2f949a07
source-git-commit: 7785a37e033bc2bea5b6a1509c337289e7b871cb
workflow-type: tm+mt
source-wordcount: '487'
ht-degree: 0%

---

# [!DNL UPS] migração da integração do método de envio do [!DNL SOAP] para [!DNL RESTful API]

>[!NOTE]
>
>Se você tiver carregado algum dos três patches deste artigo antes de **10 de outubro de 2023**, você deve reaplicar um desses patches agora publicados neste artigo para a versão 2.4.4+/2.4.5+/2.4.6+ do Adobe Commerce/Magento Open Source mais uma vez, caso contrário, não será possível selecionar e configurar patches específicos [!DNL UPS] métodos de envio na **[!DNL Admin configuration]**, e você precisará ter todos eles habilitados. Esses novos patches são compatíveis com os patches lançados anteriormente.

Este artigo fornece uma correção para resolver problemas com o [!DNL United Parcel Service (UPS)] migração da integração do método de envio do [!DNL SOAP] para [!DNL RESTful API] para Adobe Commerce 2.4.4 - 2.4.6-pX.

De acordo com as últimas atualizações do [!DNL UPS API] Modelo de segurança, [!DNL UPS] implementou um [!DNL OAuth 2.0] modelo de segurança para todos [!DNL APIs] (Mais detalhes disponíveis na [[!DNL UPS] Guia de migração da chave de acesso do portal do desenvolvedor](https://developer.ups.com/oauth-developer-guide?loc=en_US&amp;sp_rid=NTA5MzQ1OTE2NjEyS0&amp;sp_mid=72989914)) para aumentar a segurança geral, a fim de reduzir a fraude e [!DNL API] recursos.

Essa alteração afeta nossa [!DNL UPS] implementação da integração do método de envio no Adobe Commerce e exige que corrijamos nossa implementação atual e migremos do [!DNL SOAP API] para o [!DNL RESTful API] para poder dar suporte [!DNL OAuth 2.0] protocolos de autenticação.

**A partir de junho de 2024**, os comerciantes do Adobe Commerce não poderão fazer transações com nossos clientes atuais [!DNL UPS] integração, então estamos lançando este hotfix, que permite que os comerciantes do Adobe Commerce 2.4.4+/2.4.5+/2.4.6+ migrem para a versão mais recente [!DNL UPS REST APIs].

Esse problema será corrigido no Adobe Commerce/Magento Open Source versão 2.4.7 e a correção também será incluída na versão 2.4.7-beta2 em outubro de 2023.

## Produtos e versões afetados

Adobe Commerce na infraestrutura em nuvem e no local, e Magento Open Source:

* 2.4.4
* 2,4,4-pX
* 2.4.5
* 2,4,5-pX
* 2.4.6
* 2,4,6-pX

## Causa

A variável [!DNL UPS] liberou um [atualização de segurança para seus [!DNL API]](https://developer.ups.com/oauth-developer-guide?loc=en_US&amp;sp_rid=NTA5MzQ1OTE2NjEyS0&amp;sp_mid=72989914).

## Solução

Use os seguintes patches anexados, dependendo da sua versão do Adobe Commerce/Magento Open Source:

Para resolver o problema nas versões 2.4.4+, 2.4.5+ e 2.4.6+, você deve aplicar o patch correspondente à versão do Adobe Commerce/Magento Open Source abaixo.

## Correção

Use os seguintes patches anexados, dependendo da sua versão do Adobe Commerce/Magento Open Source:

### Para as versões 2.4.4, 2.4.4-pX:

* [AC-9363_UPS_Shipping_Method_Migration_REST_API_2.4.4x_COMPOSER.patch.zip](assets/AC-9646_UPS_Shipping_Method_Migration_REST_API_2.4.4x_COMPOSER.patch.zip)

### Para as versões 2.4.5, 2.4.5-pX:

* [AC-9358_UPS_Shipping_Method_Migration_REST_API_2.4.5x_COMPOSER.patch.zip](assets/AC-9647_UPS_Shipping_Method_Migration_REST_API_2.4.5x_COMPOSER.patch.zip)

### Para as versões 2.4.6, 2.4.6-pX:

* [AC-9345_UPS_Shipping_Method_Migration_REST_API_2.4.6x_COMPOSER.patch.zip](assets/AC-9648_UPS_Shipping_Method_Migration_REST_API_2.4.6x_COMPOSER.patch.zip)

## Como aplicar o patch

Descompacte o arquivo e veja [Como aplicar um patch de compositor fornecido pelo Adobe](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento.html) na nossa base de conhecimento de suporte para obter instruções.

## Como saber se os patches foram aplicados

Considerando que não é possível verificar facilmente se o problema foi corrigido, talvez você queira verificar se o patch foi aplicado com sucesso. Isso usa (Exemplo: *AC-9363*) como o patch a ser verificado.

<u>Você pode fazer isso executando as seguintes etapas</u>:

1. [Instale o [!DNL Quality Patches Tool]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html).
1. Execute o comando:

   ```bash
   vendor/bin/magento-patches -n status |grep "9363|Status"
   ```

1. Você deve ver uma saída semelhante a esta, em que AC-9363 retorna a variável *Aplicado* Status:

   ```bash
   ║ Id            │ Title                                                        │ Category        │ Origin                 │ Status      │ Details                                          ║ ║ N/A           │ ../m2-hotfixes/AC-9363_USPS_Ground_Advantage_shipping_method_COMPOSER_patch.patch      │ Other           │ Local                  │ Applied     │ Patch type: Custom                                
   ```
