---
title: '[!DNL FedEx] migração de integração do método de envio de SOAP para RESTful API'
promoted: true
description: Aplique uma correção para lidar com a [!DNL FedEx] migração de integração de método de envio do SOAP para a API RESTful para Adobe Commerce 2.4.4-p4 - 2.4.6-pX.
feature: Shipping/Delivery
role: Developer
exl-id: 7e11a171-6924-41d0-a5c7-7b794d0da84c
source-git-commit: 7c468583883789a6bc6e41d1a787a356ea3205c4
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 0%

---

# [!DNL FedEx] migração da integração do método de envio de SOAP para RESTful API

Este artigo fornece uma correção para resolver problemas com o [!DNL FedEx] migração de integração de método de envio do SOAP para a API RESTful para Adobe Commerce 2.4.4-p4 - 2.4.6-pX.

[!DNL FedEx Web Services] O rastreamento do, a Validação de endereço e a Validação de códigos postais dos Idiomas de definição de serviços da Web (WSDLS) serão desativados em 15 de maio de 2024. O baseado em SOAP [!DNL FedEx Web Services] está em contenção de desenvolvimento e foi substituída por [!DNL FedEx] RESTFUL APIs. Para saber mais, consulte [[!DNL FedEx Web Services]](https://www.fedex.com/en-us/developer/web-services.html).

Essa alteração afeta nossa [!DNL FedEx] implementação da integração do método de envio no Adobe Commerce e exige que corrijamos nossa implementação atual e migremos de APIs SOAP obsoletas para a mais recente [!DNL FedEx] RESTFUL APIs.

A partir de 15 de maio de 2024, os clientes do Adobe Commerce não poderão usar nosso atual [!DNL FedEx] integração do método de envio, portanto, a Adobe está lançando essa correção que permite aos clientes do Adobe Commerce 2.4.4+ usar a versão mais recente [!DNL FedEx] APIs RESTFUL em vez das SOAP obsoletas.


## Produtos e versões afetados

Adobe Commerce na infraestrutura em nuvem e no local, e Magento Open Source:

* 2.4.4-p4
* 2.4.5
* 2,4,5-pX
* 2.4.6
* 2,4,6-pX

## Causa

A variável [!DNL FedEx] substituíram as APIs baseadas em SOAP pelas RESTful. Consulte [[!DNL FedEx Web Services]](https://www.fedex.com/en-us/developer/web-services.html).

## Solução

Use os seguintes patches anexados, dependendo da sua versão do Adobe Commerce/Magento Open Source:

Para resolver o problema nas versões 2.4.4+, 2.4.5+ e 2.4.6+, você deve aplicar o patch correspondente à versão do Adobe Commerce/Magento Open Source abaixo.

## Correção

Use os seguintes patches anexados, dependendo da sua versão do Adobe Commerce/Magento Open Source:

### Para as versões 2.4.4-p4:

* [FedexPatch-Composer-245p5-244p6develop.patch.zip](assets/FedexPatch-Composer-245p5-244p6develop.patch.zip)

### Para as versões 2.4.5, 2.4.5-pX:

* [FedexPatch-Composer-245p5-244p6develop.patch.zip](assets/FedexPatch-Composer-245p5-244p6develop.patch.zip)


### Para as versões 2.4.6, 2.4.6-pX:


* [FedexPatch-Composer-246p3develop.patch.zip](assets/FedexPatch-Composer-246p3develop.patch.zip)


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
