---
title: 2.3.4 Hotfix de problemas do PayPal
description: Este artigo fornece uma correção para erros recebidos durante o posicionamento do pedido ao selecionar uma região no Check-out expresso do PayPal. O problema é causado pelas alterações feitas na versão 2.3.4 do Adobe Commerce e está relacionado à forma como os campos de endereço de Finalização de compra do PayPal Express são analisados.
exl-id: 9f5ec100-49b0-4ac5-8951-32b5c4fe6bed
feature: Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# 2.3.4 Hotfix de problemas do PayPal

Este artigo fornece uma correção para erros recebidos durante o posicionamento do pedido ao selecionar uma região no Check-out expresso do PayPal. O problema é causado pelas alterações feitas na versão 2.3.4 do Adobe Commerce e está relacionado à forma como os campos de endereço de Finalização de compra do PayPal Express são analisados.

## Versões e produtos afetados

* Adobe Commerce na infraestrutura em nuvem v2.3.4
* Adobe Commerce no local v2.3.4

## Problema

Ocorre um erro ao entrar no país e na região durante o envio do pedido no Check-out expresso do PayPal. O problema pode ser reproduzido em qualquer país em que o campo de região na seção de endereço seja um campo de texto (em vez de um menu suspenso).

<u>Etapas a serem reproduzidas</u> :

1. Ative o Check-out expresso do PayPal.
1. Adicione o produto ao carrinho como convidado ou quando estiver conectado.
1. Vá para o check-out.
1. Selecione o endereço de entrega. Por exemplo, a variável *Reino Unido* . Em seguida, insira uma entrada na variável **Estado/Província** campo. Por exemplo, *Nottinghamshire*.
1. Clique no link **Fazer pedido** botão para colocar a ordem. Você recebe uma página de pedido bem-sucedida e um email de confirmação de pedido.

<u>Resultado esperado:</u>

O pedido foi feito com sucesso.

<u>Resultado Real:</u>

Quando o botão do pedido é clicado, um erro é exibido:

```
Error 500: NOTICE: PHP message: PHP Fatal error: Uncaught Error: Call to a member
  function getId() on null in httpdocs/vendor/magento/module-paypal/Model/Api/Nvp.php:1527
```

## Solução

Para comerciantes locais do Adobe Commerce: aplique o [hotfix,](https://magento.com/tech-resources/download#download2353) que está disponível na seção Downloads em [magento.com](https://magento.com) portal em Minha conta.

Para o Adobe Commerce em comerciantes de infraestrutura em nuvem: o Adobe incluiu a correção nos Patches da nuvem para o Commerce v1.0.2. Consulte [Notas de versão do Cloud Patches for Commerce](https://devdocs.magento.com/cloud/release-notes/mcp-release-notes.html?itm_source=devdocs&amp;itm_medium=quick_search&amp;itm_campaign=federated_search&amp;itm_term=cloud%20patche) na documentação do desenvolvedor, para encontrar instruções sobre como aplicar o pacote mais recente.

## Como aplicar o patch

Para obter instruções, consulte [Como aplicar um patch de compositor fornecido pelo Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) em nossa base de conhecimento de suporte.

## Leitura relacionada

* [Informações de versão > Notas de versão do Adobe Commerce 2.3.4 > Aplicar o problema do Check-out do PayPal Express com patch de região para o Adobe Commerce 2.3.4 para resolver um problema crítico do Check-out do PayPal Express](https://devdocs.magento.com/guides/v2.3/release-notes/release-notes-2-3-4-commerce.html#apply-the-paypal-express-checkout-issue-with-region-patch-for-magento-234-to-address-a-critical-paypal-express-checkout-issue) na documentação do desenvolvedor.
