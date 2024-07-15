---
title: Migração da integração do método de envio [!DNL FedEx] do SOAP para a API RESTful
promoted: true
description: Aplique um patch para lidar com a migração de integração do método de envio  [!DNL FedEx]  do SOAP para a API RESTful para Adobe Commerce 2.4.4-p4 - 2.4.6-pX.
feature: Shipping/Delivery
role: Developer
exl-id: 7e11a171-6924-41d0-a5c7-7b794d0da84c
source-git-commit: 7c468583883789a6bc6e41d1a787a356ea3205c4
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 0%

---

# Migração da integração do método de envio [!DNL FedEx] do SOAP para a API RESTful

Este artigo fornece uma correção para resolver problemas com a migração de integração do método de envio [!DNL FedEx] do SOAP para a API RESTful para Adobe Commerce 2.4.4-p4 - 2.4.6-pX.

O rastreamento de [!DNL FedEx Web Services], a Validação de Endereço e a Validação de WSDLS (Idiomas de Definição de Serviços Web) de Códigos Postais serão desativados em 15 de maio de 2024. O [!DNL FedEx Web Services] baseado em SOAP está em contenção de desenvolvimento e foi substituído por [!DNL FedEx] APIs RESTFUL. Para saber mais, consulte [[!DNL FedEx Web Services]](https://www.fedex.com/en-us/developer/web-services.html).

Essa alteração afeta nossa implementação atual de integração do método de envio [!DNL FedEx] no Adobe Commerce e requer que corrijamos nossa implementação atual e migremos de APIs SOAP obsoletas para as APIs RESTFUL [!DNL FedEx] mais recentes.

A partir de 15 de maio de 2024, os clientes do Adobe Commerce não poderão usar nossa integração atual do método de envio [!DNL FedEx], portanto, o Adobe está lançando este hotfix que permite que os clientes do Adobe Commerce 2.4.4+ usem as APIs RESTFUL [!DNL FedEx] mais recentes em vez das APIs SOAP obsoletas.


## Produtos e versões afetados

Adobe Commerce na infraestrutura em nuvem e no local, e Magento Open Source:

* 2.4.4-p4
* 2.4.5
* 2,4,5-pX
* 2.4.6
* 2,4,6-pX

## Causa

O [!DNL FedEx] descontinuou suas APIs baseadas em SOAP e as substituiu pelas RESTful. Consulte [[!DNL FedEx Web Services]](https://www.fedex.com/en-us/developer/web-services.html).

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
