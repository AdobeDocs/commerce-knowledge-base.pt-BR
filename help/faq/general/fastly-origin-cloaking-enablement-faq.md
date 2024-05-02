---
title: "[!DNL Fastly] perguntas frequentes sobre a ativação de cloaking de origem"
description: Estas Perguntas frequentes abordam perguntas comuns sobre [!DNL Fastly] ativação do cloaking de origem no Adobe Commerce (que foi totalmente implementada a partir de 2021).
exl-id: d608abe7-7d64-44ce-bea1-34b201c29113
source-git-commit: 348a1f6e455aff9ad7c562ea20c95f27c9ee0b86
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 0%

---

# [!DNL Fastly] Perguntas frequentes sobre a ativação de cloaking de origem

Estas Perguntas frequentes abordam perguntas comuns sobre [!DNL Fastly] ativação do cloaking de origem no Adobe Commerce (que foi totalmente implementada a partir de 2021).

## O que é o [!DNL Fastly] cloaking de origem?

O cloaking de origem é um recurso de segurança que permite que o Adobe Commerce na infraestrutura em nuvem bloqueie qualquer [!DNL non-Fastly] tráfego (para evitar ataques de DDoS, vá para a infraestrutura em nuvem (origem).

## Quais são os benefícios do cloaking de origem?

O cloaking de origem é projetado para impedir que o tráfego ignore o [!DNL Fastly Web Application Firewall] (WAF) e roteá-lo pelo fluxo estritamente definido de **[!DNL Fastly]** > **Balanceador de carga** > **Instâncias**. Com essa implementação, todo o tráfego passará pelo [!DNL Fastly] O WAF e o WAF interno integrados no balanceador de carga.

## Por que essa ativação de cloaking de origem está acontecendo?

Esse recurso foi criado originalmente para beneficiar o Adobe Commerce na infraestrutura em nuvem.

## Preciso solicitar a ativação do encobrimento de origem para meu projeto?

Não. Esse recurso já deveria ter sido implementado em todos os projetos na nuvem, e qualquer projeto que tenha sido provisionado desde 2021 teria isso ativado por padrão. No entanto, você pode solicitar que o encobrimento de origem seja desativado para o seu projeto até [enviar uma solicitação de suporte](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket).

## O cloaking de origem altera o endereço IP de saída?

Não, não tem.

## O encobrimento de origem afeta a API REST?

[!DNL Fastly] O não armazena chamadas de API em cache, portanto, o cliente deve estar preparado para a alteração. O cloaking de origem bloqueia somente solicitações que vão diretamente para a origem, como:

```php
mywebsite.com.c.abcdefghijkl.ent.magento.cloud
```

Neste exemplo, o cliente ainda poderá acessar a API se alterar o URL para ``mywebsite.com``:

```php
mywebsite.com/rest/default/V1/integration/admin/token?username=XXXX&password=XXXXX;
mywebsite.com/rest/default/V1/orders/
mywebsite.com/rest/default/V1/products/
mywebsite.com/rest/default/V1/inventory/source-items
```

## Essa alteração afetará a implantação e o tempo de inatividade?

Não, essa alteração **NOT** afetam a implantação e o tempo de inatividade.

## Se o projeto tiver vários ambientes de preparo, o cloaking de origem será aplicado a todos os ambientes de preparo?

Sim, se o projeto tiver vários ambientes de preparo, a alteração será aplicada a todos os ambientes de preparo.
