---
title: 2.3.4 Hotfix de problemas do PayPal
description: Este artigo fornece uma correção para erros recebidos durante o posicionamento do pedido ao selecionar uma região no Check-out expresso do PayPal. O problema é causado pelas alterações feitas na versão 2.3.4 do Adobe Commerce e está relacionado à forma como os campos de endereço de Finalização de compra do PayPal Express são analisados.
exl-id: 9f5ec100-49b0-4ac5-8951-32b5c4fe6bed
feature: Orders, Payments
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
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

<u>Etapas a serem reproduzidas</u>:

1. Ative o Check-out expresso do PayPal.
1. Adicione o produto ao carrinho como convidado ou quando estiver conectado.
1. Vá para o check-out.
1. Selecione o endereço de entrega. Por exemplo, o *Reino Unido*. Em seguida, insira uma entrada no campo **Estado/Província**. Por exemplo, *Nottinghamshire*.
1. Clique no botão **Fazer pedido** para fazer o pedido. Você recebe uma página de pedido bem-sucedida e um email de confirmação de pedido.

<u>Resultado Esperado:</u>

O pedido foi feito com sucesso.

<u>Resultado Real:</u>

Quando o botão do pedido é clicado, um erro é exibido:

```
Error 500: NOTICE: PHP message: PHP Fatal error: Uncaught Error: Call to a member
  function getId() on null in httpdocs/vendor/magento/module-paypal/Model/Api/Nvp.php:1527
```

## Solução

Para comerciantes locais do Adobe Commerce: aplique o [hotfix](https://magento.com/tech-resources/download#download2353), que está disponível na seção Downloads do portal [magento.com](https://magento.com) em Minha conta.

Para o Adobe Commerce em comerciantes de infraestrutura em nuvem: o Adobe incluiu a correção nos Patches da nuvem para o Commerce v1.0.2. Consulte [Patches da nuvem para as notas de versão do Commerce](https://experienceleague.adobe.com/pt-br/docs/commerce-cloud-service/user-guide/release-notes/cloud-patches?itm_source=devdocs&amp;itm_medium=quick_search&amp;itm_campaign=federated_search&amp;itm_term=cloud%20patche) em nossa documentação do desenvolvedor para encontrar instruções sobre como aplicar o pacote mais recente.

## Como aplicar o patch

Para obter instruções, consulte [Como aplicar um patch de compositor fornecido pelo Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) em nossa base de dados de conhecimento de suporte.

## Leitura relacionada

* [Informações de versão > Notas de versão do Adobe Commerce 2.3.4 > Aplicar o problema do Check-out expresso do PayPal com patch de região para Adobe Commerce 2.3.4 para resolver um problema crítico do Check-out expresso do PayPal](https://commerce-docs.github.io/devdocs-archive/2.3/guides/v2.3/release-notes/release-notes-2-3-4-commerce.html#apply-the-paypal-express-checkout-issue-with-region-patch-for-magento-234-to-address-a-critical-paypal-express-checkout-issue) em nossa documentação do desenvolvedor.
