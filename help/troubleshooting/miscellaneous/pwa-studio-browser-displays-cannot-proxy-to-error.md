---
title: 'PWA Studio: O navegador exibe o erro "Não é possível usar proxy para"'
description: Este tópico discute uma solução quando o navegador da Web exibe um "*Não é possível usar proxy para*" e o console exibe um
exl-id: de689633-34b8-4a25-bbd0-a58742c4d03c
feature: Console
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '187'
ht-degree: 0%

---

# PWA Studio: O navegador exibe o erro &quot;Não é possível usar proxy para&quot;

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

* [PWA Studio para a documentação do Adobe Commerce](https://magento.github.io/pwa-studio/)
* [Ferramentas e bibliotecas](https://magento.github.io/pwa-studio/technologies/tools-libraries/)
