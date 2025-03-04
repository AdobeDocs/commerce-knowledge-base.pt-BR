---
title: O sistema Magento Order Management (OMS) para Adobe Commerce atinge o tempo limite
description: Este artigo fornece uma solução para o problema em que o Sistema de Magento Order Management (OMS) para Adobe Commerce não pode registrar o microsserviço instalado localmente no MOM usando ngrok, pois o MOM atinge o tempo limite ao tentar fazer o retorno de chamada.
exl-id: 19149d8c-ea24-46fb-8815-9f637afe46ca
feature: System
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '223'
ht-degree: 0%

---

# O sistema Magento Order Management (OMS) para Adobe Commerce atinge o tempo limite

Este artigo fornece uma solução para o problema em que o Sistema de Magento Order Management (OMS) para Adobe Commerce não pode registrar o microsserviço instalado localmente no MOM usando ngrok, pois o MOM atinge o tempo limite ao tentar fazer o retorno de chamada.

## Produtos e versões afetados

* Adobe Commerce 2.3.1
* OMS
* grok

>[!WARNING]
>
>Isenção de responsabilidade: a Adobe Commerce não recomenda nem endossa nenhuma ferramenta específica para o estabelecimento de túneis. As anteriores são apenas sugestões. Para obter mais informações, consulte a [ngrok documentation](https://ngrok.com/docs).

## Problema

<u>Etapas a serem reproduzidas</u>

1. Instale o Adobe Commerce em seu ambiente local.
1. Configure o ngrok para criar um túnel para expor seu servidor local.
1. Tente [conectar-se ao OMS](https://commerce-docs.github.io/oms-documentation-archive/integration/connector/setup-tutorial/).

<u>Resultado esperado</u>

Conexão estabelecida com sucesso.

<u>Resultado real</u>

O MCOM parece expirar o tempo limite ao tentar chamar de volta a URL do Grok.

## Causa

Uma das possíveis razões para o tempo limite é que os servidores estão localizados geograficamente muito longe e a conexão leva muito tempo.

## Solução

Adicione um parâmetro especificando sua região ao iniciar o ngrok. Como o seguinte:

```bash
./ngrok http 80 -region eu
```

A região padrão é EUA. Consulte [todos os valores possíveis](https://ngrok.com/docs#config_region).
