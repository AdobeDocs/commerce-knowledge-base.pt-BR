---
title: O cupom para uso único é usado várias vezes, Adobe Commerce
description: Este artigo fornece uma solução para o problema que ocorre quando os cupons da regra de preço do carrinho não estão funcionando corretamente. Os comerciantes configuram um cupom para uso único e os clientes podem usá-lo várias vezes.
exl-id: 9c81de40-65a3-422d-9053-3c894b863a0a
feature: Orders
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 0%

---

# O cupom para uso único é usado várias vezes, Adobe Commerce

Este artigo fornece uma solução para o problema que ocorre quando os cupons da regra de preço do carrinho não estão funcionando corretamente. Os comerciantes configuram um cupom para uso único e os clientes podem usá-lo várias vezes.


## Produtos e versões afetados

Adobe Commerce (todos os métodos de implantação) 2.4.3 e superior

## Problema

Os comerciantes configuram um cupom para uso único e os clientes podem usá-lo várias vezes.

<u>Etapas a serem reproduzidas</u>:

1. Crie um cupom e configure o cupom para uso único.
1. Prossiga para o check-out.
1. Use o cupom que acabou de criar.
1. Continue com o check-out novamente e use o mesmo cupom.

<u>Resultado esperado</u>:

O cupom só pode ser usado uma vez. Uma mensagem é exibida: *O código do cupom &quot;COUPON_NAME&quot; não é válido*.

<u>Resultado real</u>:

O cupom pode ser usado mais de uma vez.


## Causa

Os comerciantes não têm o consumidor `sales.rule.update.coupon.usage` configurado e em execução, o que resulta em comportamento inadequado.

## Solução

Adicionar o consumidor `sales.rule.update.coupon.usage` ao arquivo `app/etc/env.php`.

```php
...
    'cron_consumers_runner' =>
    array [
        'cron_run' => true,
        'max_messages' => 20000,
        'consumers' =>
        array [
            'sales.rule.update.coupon.usage'
        ]
    ],
...
```

Para obter etapas detalhadas, consulte [Gerenciar filas de mensagens > Configuração](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/configuration-guide/message-queues/manage-message-queues#configuration) na documentação do desenvolvedor.

## Leitura relacionada

[Visão geral das filas de mensagens](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/configuration-guide/message-queues/message-queue-framework) na documentação do desenvolvedor.
