---
title: Erro 503 ao acessar o Adobe Commerce no navegador da web
description: Este artigo fornece uma solução possível para o problema em que você recebe um erro 503 ao tentar acessar a loja e/ou o administrador do Adobe Commerce.
exl-id: 4232aa21-40c2-41b0-9fb0-fc8cd4db8e39
feature: Storefront
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '204'
ht-degree: 0%

---

# Erro 503 ao acessar o Adobe Commerce no navegador da web

Este artigo fornece uma solução possível para o problema em que você recebe um erro 503 ao tentar acessar a loja e/ou o administrador do Adobe Commerce.

## Produtos e versões afetados

Adobe Commerce 2.3.x

## Problema {#symptoms}

<u>Etapas a serem reproduzidas</u>

(Pré-requisitos: verifique se o repositório não está no [modo de manutenção](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/set-mode#config-mode-show)).

Navegue até o administrador do Commerce ou a loja em um navegador da Web.

<u>Resultado esperado</u>

A página é carregada.

<u>Resultado real</u>

Você recebe o erro HTTP 503 (Serviço indisponível). O Apache `error.log` inclui a seguinte mensagem:

*Comando &#39;Ordem&#39; inválido, talvez com ortografia incorreta ou definido por um módulo não incluído na configuração do servidor.*

## Causa {#details}

O módulo de compatibilidade `mod_access_compat` do Apache 2.4 está desabilitado, o que resulta em regravações de URL Adobe Commerce não funcionando corretamente.

## Solução {#suggested-solution}

Habilite o módulo Apache `mod_access_compat` e reinicie o Apache, executando o seguinte como um usuário com privilégios &#39;root&#39;:

```bash
a2enmod access_compat
service <name> restart
```

No CentOS,

```bash
<name>
```

é

```bash
httpd
```

. No Ubuntu,

```bash
<name>
```

é

```bash
apache2
```

.

## Leitura relacionada {#additional-resources}

* [Documentação do Apache sobre mod\_access\_compat](https://httpd.apache.org/docs/current/mod/mod_access_compat.html)
* [Documentação do Apache sobre mod\_authz\_host](https://httpd.apache.org/docs/current/mod/mod_authz_host.html)
* [Pedir, Permitir, Negar no Guia Definitivo do Apache](https://docstore.mik.ua/orelly/linux/apache/ch05_06.htm)
* [askubuntu.com](https://askubuntu.com/questions/335228/changes-in-apache-config-between-12-04-2-and-12-04-3-lts)
