---
title: 'PWA Studio: o navegador exibe o erro "Não é possível usar proxy para"'
description: Este tópico discute uma solução quando o navegador da Web exibe um "*Não é possível usar proxy para*" e o console exibe um
exl-id: de689633-34b8-4a25-bbd0-a58742c4d03c
feature: Console
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
subfeature_v2:
  - id: c4af0798-d497-5e6b-8380-19812c26d00a
    internal-label: Console
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '207'
ht-degree: 0%
---
# PWA Studio: o navegador exibe o erro &quot;Não é possível usar proxy para&quot;

Este tópico discute uma solução quando o navegador da Web exibe um &quot;*Não é possível usar proxy para*&quot; e o console exibe um

```
ENOTFOUND
```

erro ao usar o Progressive Web App (PWA) Studio para Adobe Commerce.

## Produtos e versões afetados

* PWA Studio para Adobe Commerce

## Problema

<u>Etapa de reprodução</u>:

* Carregue sua loja Adobe Commerce em um navegador.

<u>Resultado esperado</u>:

* A loja da Adobe Commerce é carregada normalmente no navegador.

<u>Resultado real</u>:

* Seu navegador da Web exibe o erro &quot;*Não é possível intermediar para*&quot; e o console exibe um erro como:

```
    ENOTFOUND
```


## Causa

O NodeJS não pode resolver o nome do host de seu armazenamento do Adobe Commerce.

## Solução

1. Certifique-se de que o armazenamento do Adobe Commerce seja carregado em mais de um navegador da Web.
1. Se você estiver executando um servidor DNS ou VPN local, adicione uma entrada ao arquivo de host (localizado em `/etc/hosts`) e mapeie manualmente esse domínio ([Instruções genéricas sobre a edição do arquivo de host](https://linuxize.com/post/how-to-edit-your-hosts-file/)) para que o NodeJS possa resolvê-lo.

## Leitura relacionada

* [Documentação do PWA Studio para Adobe Commerce](https://developer.adobe.com/commerce/pwa-studio/)
* [Ferramentas e bibliotecas](https://developer.adobe.com/commerce/pwa-studio/guides/project/tools-libraries/)
