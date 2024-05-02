---
title: "ERRO: falha no aquecimento do Adobe Commerce na infraestrutura em nuvem"
description: "Este artigo fornece uma solução para quando o cache da página está sendo aquecido e falha com um erro:"
exl-id: 20a88030-b1c9-4fdc-83c1-f344d44cd2e1
feature: Cache, Cloud, Paas
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '188'
ht-degree: 0%

---

# ERRO: falha no aquecimento do Adobe Commerce na infraestrutura de nuvem

Este artigo fornece uma solução para quando o cache da página está sendo aquecido e falha com um erro:

*ERRO: falha no aquecimento:`<website link>`*

## Produtos e versões afetados

* Adobe Commerce na infraestrutura em nuvem, tudo [versões compatíveis](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Problema

Falha no aquecimento de cache.

<u>Etapas a serem reproduzidas</u>:

Iniciar operações de aquecimento do cache.

<u>Resultado esperado</u>:

Páginas ou todo o site é carregado.

<u>Resultado real</u>:

O site não está disponível ou o tempo de resposta é muito alto. *ERRO: falha no aquecimento:`<website link>`*

## Causa

O aquecimento de cache não funciona com o controle de acesso HTTP ativado.

## Solução

Certifique-se de que o controle de acesso não está ativado: vá para a ramificação/ambiente específico e clique no **Configurações** e marque a opção **Controle de acesso HTTP** configuração - o aquecimento do cache não pode ocorrer neste cenário e o controle de acesso deve ser desabilitado.

## Leitura relacionada

* [Guia do usuário do Adobe Commerce > Cache de página inteira](https://docs.magento.com/user-guide/system/cache-full-page.html) em nosso guia do usuário.
* [Aquecimento de cache e site indisponível no Adobe Commerce](/help/troubleshooting/miscellaneous/cache-warming-up-and-site-unavailable-on-magento.md) em nossa base de conhecimento de suporte.
