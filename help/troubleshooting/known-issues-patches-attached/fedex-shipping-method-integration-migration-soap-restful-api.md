---
title: Migração da integração do método de envio [!DNL FedEx] do SOAP para a API RESTful
promoted: true
description: Aplique um patch para lidar com a migração de integração do método de envio  [!DNL FedEx]  do SOAP para a API RESTful para Adobe Commerce 2.4.4-p4 - 2.4.6-pX.
feature: Shipping/Delivery
role: Developer
exl-id: 7e11a171-6924-41d0-a5c7-7b794d0da84c
source-git-commit: 7a54e992e365238ec7c764225a31cd3b6b8ad019
workflow-type: tm+mt
source-wordcount: '482'
ht-degree: 0%

---

# Migração da integração do método de envio [!DNL FedEx] do SOAP para a API RESTful

>[!WARNING]
>
>Use o patch ACSD-61622 da versão 1.1.57 do [!DNL Quality Patches Tool] (QPT) em vez do patch fornecido anteriormente. O novo patch é compatível com as versões do Adobe Commerce (todos os métodos de implantação) 2.4.6-p1 - 2.4.6-p8. Ela pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool].
>
>Para obter mais informações, consulte o [artigo de correção ACSD-61622](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-57/acsd-61622-fedex-account-specific-rates-missing-from-response) em nosso Guia de ferramentas do Adobe Commerce.

>[!WARNING]
>
>Antes de instalar o novo patch, é necessário desinstalar o patch anterior fornecido neste artigo. Para obter instruções sobre como desinstalar patches, consulte [Reverter um patch personalizado](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches#revert-a-custom-patch) no guia do usuário.


Este artigo fornece uma correção para resolver problemas com a migração de integração do método de envio [!DNL FedEx] do SOAP para a API RESTful para Adobe Commerce 2.4.4-p4 - 2.4.6-pX.

O rastreamento do [!DNL FedEx Web Services], a Validação de Endereço e a Validação de WSDLS (Web Services Definition Languages) de Códigos Postais foram removidos em 15 de maio de 2024. O [!DNL FedEx Web Services] baseado em SOAP está em contenção de desenvolvimento e foi substituído por [!DNL FedEx] APIs RESTFUL. Para saber mais, consulte [[!DNL FedEx Web Services]](https://www.fedex.com/en-us/developer/web-services.html).

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
