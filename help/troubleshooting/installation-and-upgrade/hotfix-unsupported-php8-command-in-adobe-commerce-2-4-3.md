---
title: Hotfix de erro fatal do PHP 2.4.3, 2.3.7-p1 para Adobe Commerce
description: 'Este artigo fornece uma correção para quando os comerciantes tentam atualizar para o Adobe Commerce (todos os métodos de implantação) ou para o Magento Open Source 2.4.3 ou 2.3.7-p1; o seguinte erro é exibido:'
exl-id: 1c472214-8387-403e-b2d2-d3f3c9e1da6a
feature: Install, Upgrade
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 6388cf7b-8a81-5248-a1e4-7bb57bbe250f
    internal-label: Install
  - id: a8ae7a5a-6cdc-5922-bd0d-6feb44b04984
    internal-label: Upgrade
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 0%
---
# Hotfix de erro fatal do PHP 2.4.3, 2.3.7-p1 para Adobe Commerce

Este artigo fornece uma correção para quando os comerciantes tentam atualizar para o Adobe Commerce (todos os métodos de implantação) ou para o Magento Open Source 2.4.3 ou 2.3.7-p1; o seguinte erro é exibido:

*Erro fatal de PHP: Erro não capturado: chamada para função indefinida Magento\Framework\Filesystem\Directory\str_contains() em &lt;...>/magento/vendor/magento/framework/Filesystem/Directory/DenyListPathValidator.php:74*

O problema será corrigido no escopo das versões 2.4.4, 2.4.3-p1 e 2.3.7-p2.

## Versões e produtos afetados

* Adobe Commerce (todos os métodos de implantação) ao atualizar para 2.3.7-p1 ou 2.4.3.
* Magento Open Source ao atualizar para 2.3.7-p1 ou 2.4.3.

## Problema

O problema é causado pelas novas versões do Adobe Commerce 2.4.3 e 2.3.7-p1 usando apenas a função `str_contains` do PHP 8. Adobe Commerce 2.4.3 e 2.3.7-p1 só são compatíveis com o PHP 7.4, então esta função não pode ser usada.

<u>Etapas a serem reproduzidas</u>:

Tente atualizar para o Adobe Commerce 2.4.3 ou 2.3.7-p1.

<u>Resultado esperado:</u>

Atualização bem-sucedida.

<u>Resultado real:</u>

Erro fatal do PHP.

## Solução

Como solução alternativa, você executa o seguinte comando no CLI/Terminal: `composer require symfony/polyfill-php80` da pasta raiz da Magento ou instala um patch de compositor.

Para corrigir o problema da versão 2.4.3, o Adobe Commerce (todos os métodos de implantação) e os comerciantes do Magento Open Source devem aplicar o patch:

[AC-384_Fix_Incompatible_PHP_Method__2.4.3_ce.patch](assets/AC-384__Fix_Incompatible_PHP_Method__2.4.3_ce.patch.zip)

Para corrigir o problema da versão 2.3.7-p1, a Adobe Commerce (todos os métodos de implantação) e os comerciantes da Magento Open Source devem aplicar o patch:

[AC-384_Fix_Incompatible_PHP_Method_2.3.7-p1_ce.patch](assets/AC-384__Fix_Incompatible_PHP_Method__2.3.7-p1_ce.patch.zip)

## Como aplicar o patch

Consulte [Como aplicar um patch de compositor fornecido pela Magento](https://experienceleague.adobe.com/pt-br/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/how-to-apply-a-composer-patch-provided-by-magento) para obter instruções.

## Leitura relacionada

GitHub [Comando do PHP 8 sem suporte na Magento 2.4.3 EE #33680](https://github.com/magento/magento2/issues/33680)
