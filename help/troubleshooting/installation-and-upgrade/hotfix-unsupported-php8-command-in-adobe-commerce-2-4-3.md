---
title: Hotfix de erro fatal do PHP 2.4.3, 2.3.7-p1 para Adobe Commerce
description: "Este artigo fornece uma correção para quando os comerciantes tentam atualizar para o Adobe Commerce (todos os métodos de implantação) ou para o Magento Open Source 2.4.3 ou 2.3.7-p1; o seguinte erro é exibido:"
exl-id: 1c472214-8387-403e-b2d2-d3f3c9e1da6a
feature: Install, Upgrade
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 0%

---

# Hotfix de erro fatal do PHP 2.4.3, 2.3.7-p1 para Adobe Commerce

Este artigo fornece uma correção para quando os comerciantes tentam atualizar para o Adobe Commerce (todos os métodos de implantação) ou para o Magento Open Source 2.4.3 ou 2.3.7-p1. O seguinte erro é exibido:

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

Como solução alternativa, você executa o seguinte comando no CLI/Terminal: `composer require symfony/polyfill-php80` da pasta raiz do Magento ou instala um patch de compositor.

Para corrigir o problema da versão 2.4.3, o Adobe Commerce (todos os métodos de implantação) e os comerciantes de Magento Open Source devem aplicar o patch:

[AC-384_Fix_Incompatible_PHP_Method__2.4.3_ce.patch](assets/AC-384__Fix_Incompatible_PHP_Method__2.4.3_ce.patch.zip)

Para corrigir o problema da versão 2.3.7-p1, a Adobe Commerce (todos os métodos de implantação) e os comerciantes de Magento Open Source devem aplicar o patch:

[AC-384_Fix_Incompatible_PHP_Method_2.3.7-p1_ce.patch](assets/AC-384__Fix_Incompatible_PHP_Method__2.3.7-p1_ce.patch.zip)

## Como aplicar o patch

Consulte [Como aplicar um patch de compositor fornecido pelo Magento](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) para obter instruções.

## Leitura relacionada

GitHub [Comando PHP 8 sem suporte no Magento 2.4.3 EE #33680](https://github.com/magento/magento2/issues/33680)
