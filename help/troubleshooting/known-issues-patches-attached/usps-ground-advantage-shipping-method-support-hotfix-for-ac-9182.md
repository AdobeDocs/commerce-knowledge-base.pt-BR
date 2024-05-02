---
title: '[!DNL USPS] Hotfix de suporte do método de envio Ground Advantage para AC-9182'
promoted: true
description: Aplique uma correção para lidar com a [!DNL USPS] Problema de método de envio do Ground Advantage AC-9182 para Adobe Commerce 2.4.4 - 2.4.6-p2.
feature: Shipping/Delivery
role: Developer
exl-id: b6871d19-3d02-4026-82e6-3545f4ab7159
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 0%

---

# [!DNL USPS] Hotfix de suporte do método de envio Ground Advantage para AC-9182

Este artigo fornece um patch para resolver o problema AC-9182 para o novo **[!DNL USPS]Vantagem do solo** no Adobe Commerce 2.4.4 - 2.4.6-p2.

Em 9 De julho De 2023, O Serviço Postal Dos Estados Unidos ([!DNL USPS]) liberou um novo método de envio, [[!DNL USPS] Vantagem do solo](https://www.usps.com/ship/ground-advantage.htm).

Este novo método de envio substitui os três principais métodos de envio atuais:

* [!DNL USPS] Área de varejo
* [!DNL USPS] Serviço de pacote de primeira classe
* [!DNL USPS] Selecionar terra do pacote

[[!DNL USPS] anunciado](https://faq.usps.com/s/article/USPS-Ground-Advantage#how_it_works) que a partir de 30 de setembro de 2023, esses três métodos de envio serão descontinuados e todos os clientes deverão usar o novo **[!DNL USPS]Vantagem do solo** em vez disso.

Assim, após 30 de setembro de 2023, todos os comerciantes do Adobe Commerce que estão usando o método de envio USPS não poderão obter taxas de envio de [!DNL USPS] usando mais esses três métodos de envio herdados.

Esse problema será corrigido no escopo das próximas versões de patch somente de segurança em outubro de 2023, nas versões 2.4.6-p3, 2.4.5-p5 e 2.4.4-p6.

## Produtos e versões afetados

Adobe Commerce na infraestrutura em nuvem e no local, e Magento Open Source:

* 2.4.4
* 2.4.4-p1
* 2.4.4-p2
* 2.4.4-p3
* 2.4.4-p4
* 2.4.4-p5
* 2.4.5
* 2.4.5-p1
* 2.4.5-p2
* 2.4.5-p3
* 2.4.5-p4
* 2.4.6
* 2.4.6-p1
* 2.4.6-p2

## Causa

A variável [!DNL USPS] fez um [!DNL API] atualização.

## Solução

Para resolver o problema nas versões 2.4.4, 2.4.5 e 2.4.6, você deve aplicar o patch AC-9182 abaixo.

## Correção

O patch está anexado a este artigo. Para baixá-lo, clique no link a seguir:

[AC-9182_USPS_Ground_Advantage_shipping_method_COMPOSER_patch.zip](assets/AC-9182_USPS_Ground_Advantage_shipping_method_COMPOSER_patch.zip)

## Como aplicar o patch

Descompacte o arquivo e veja [Como aplicar um patch de compositor fornecido pelo Adobe](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento.html) na nossa base de conhecimento de suporte para obter instruções.

## Como saber se os patches foram aplicados

Considerando que não é possível verificar facilmente se o problema foi corrigido, talvez você queira verificar se o patch AC-9182 foi aplicado com sucesso.

<u>Você pode fazer isso executando as seguintes etapas</u>:

1. [Instale o [!DNL Quality Patches Tool]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html).
1. Execute o comando:

   ```bash
   vendor/bin/magento-patches -n status |grep "9182|Status"
   ```

1. Você deve ver uma saída semelhante a esta, em que AC-9182 retorna a variável *Aplicado* Status:

   ```bash
   ║ Id            │ Title                                                        │ Category        │ Origin                 │ Status      │ Details                                          ║ ║ N/A           │ ../m2-hotfixes/AC-9182_USPS_Ground_Advantage_shipping_method_COMPOSER_patch.patch      │ Other           │ Local                  │ Applied     │ Patch type: Custom                                
   ```
