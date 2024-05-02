---
title: Aplique um patch para continuar oferecendo a DHL como transportadora
description: Este artigo fornece uma correção, permitindo que os comerciantes que usam o Adobe Commerce 2.4.4 e anterior continuem oferecendo o envio para a DHL, depois que o esquema DHL 6.0 for descontinuado no final de julho a setembro de 2022.
exl-id: 4350e83a-495b-41b4-a526-dae5923e9d41
feature: Orders, Shipping/Delivery, Upgrade
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 0%

---

# Aplique um patch para continuar oferecendo a DHL como transportadora


## Produtos e versões afetados

* Adobe Commerce 2.4.4 e anterior, todos os métodos de implantação.

## Problema

A DHL está introduzindo uma versão de esquema 6.2 e substituindo a versão 6.0 até o final de julho - setembro de 2022. A integração do Adobe Commerce 2.4.4 e anterior com o DHL é compatível apenas com a versão 6.0.

## Solução

O Adobe Commerce 2.4.5, com lançamento previsto para agosto de 2022, conterá a integração atualizada com a DHL usando o schema da versão 6.2. Até que a nova versão seja lançada (ou caso você opte por não atualizar), incentivamos você a aplicar o patch AC-3022, implementando a versão 6.2 do suporte ao esquema DHL, para continuar oferecendo remessas DHL em sua loja após a desativação.

## Correção

A ID do patch é AC-3022 disponível na Ferramenta de patches de qualidade versão 1.1.16. Consulte a [Ferramenta de correção de qualidade (QPT) > Uso](https://devdocs.magento.com/quality-patches/usage.html) artigo na documentação do desenvolvedor para obter informações sobre como usar os patches QPT e instalação.

O patch é aplicável às seguintes versões do Adobe Commerce:

* 2.4.0 - 2.4.4-p1
* 2.3.7

## Leitura relacionada

* [Transportadoras > DHL](https://docs.magento.com/user-guide/shipping/dhl.html) em nosso guia do usuário
* [Métodos de delivery](https://docs.magento.com/user-guide/configuration/sales/delivery-methods.html) em nosso guia do usuário
