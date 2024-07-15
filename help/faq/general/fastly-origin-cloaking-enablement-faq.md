---
title: "[!DNL Fastly] perguntas frequentes sobre a habilitação de encobrimento de origem"
description: Estas Perguntas frequentes discutem perguntas comuns sobre a habilitação do cloaking de origem no Adobe Commerce (que foi totalmente implementado a partir de 2021). [!DNL Fastly]
exl-id: d608abe7-7d64-44ce-bea1-34b201c29113
source-git-commit: 1021a1ab81481f92e850bd49330f1742fe9a21f2
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 0%

---

# Perguntas frequentes sobre a habilitação de encobrimento de origem [!DNL Fastly]

Estas Perguntas frequentes discutem perguntas comuns sobre a habilitação do cloaking de origem do [!DNL Fastly] no Adobe Commerce (que foi totalmente implementado a partir de 2021).

## O que é cloaking de origem [!DNL Fastly]?

O cloaking de origem é um recurso de segurança que permite que o Adobe Commerce na infraestrutura em nuvem bloqueie qualquer tráfego [!DNL non-Fastly] (para evitar ataques de DDoS, indo para a infraestrutura em nuvem (origem).

## Quais são os benefícios do cloaking de origem?

O cloaking de origem foi projetado para impedir que o tráfego ignore o [!DNL Fastly Web Application Firewall] (WAF) e o encaminhe pelo fluxo estritamente definido de **[!DNL Fastly]** > **Balanceador de Carga** > **Instâncias**. Com essa implementação, todo o tráfego passará pelo WAF [!DNL Fastly], bem como pelo WAF interno integrado ao balanceador de carga.

## Por que essa ativação de cloaking de origem está acontecendo?

Esse recurso foi criado originalmente para beneficiar o Adobe Commerce na infraestrutura em nuvem.

## Preciso solicitar a ativação do encobrimento de origem para meu projeto?

Não. Esse recurso já deveria ter sido implementado em todos os projetos na nuvem, e qualquer projeto que tenha sido provisionado desde 2021 teria isso ativado por padrão.

## O cloaking de origem altera o endereço IP de saída?

Não, não tem.

## O encobrimento de origem afeta a API REST?

[!DNL Fastly] não armazena chamadas de API em cache, portanto, o cliente deve estar bem com a alteração. O cloaking de origem bloqueia somente solicitações que vão diretamente para a origem, como:

* Produção

```php
mywebsite.com.c.abcdefghijkl.ent.magento.cloud
```

* Estágios

```php
mcstaging2.mywebsite.com.c.abcdefghijkl.dev.ent.magento.cloud
```

* EstágiosX

```php
mcstagingX.mywebsite.com.c.abcdefghijkl.X.dev.ent.magento.cloud
```

Neste exemplo, o cliente ainda poderá acessar a API se alterar a URL para ``mywebsite.com``:

```php
mywebsite.com/rest/default/V1/integration/admin/token?username=XXXX&password=XXXXX;
mywebsite.com/rest/default/V1/orders/
mywebsite.com/rest/default/V1/products/
mywebsite.com/rest/default/V1/inventory/source-items
```

## Essa alteração afetará a implantação e o tempo de inatividade?

Não, essa alteração **NÃO** afetará a implantação e o tempo de inatividade.

## Se o projeto tiver vários ambientes de preparo, o cloaking de origem será aplicado a todos os ambientes de preparo?

Sim, se o projeto tiver vários ambientes de preparo, a alteração será aplicada a todos os ambientes de preparo.
