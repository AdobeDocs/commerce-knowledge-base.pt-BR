---
title: 'ERRO: falha no aquecimento do Adobe Commerce na infraestrutura de nuvem'
description: 'Este artigo fornece uma solução para quando o cache da página está sendo aquecido e falha com um erro:'
exl-id: 20a88030-b1c9-4fdc-83c1-f344d44cd2e1
feature: Cache, Cloud, Paas
role: Developer
source-git-commit: 8b6bf1cdada7edb0cdb0bb3e90ed15ee8cebf77e
workflow-type: tm+mt
source-wordcount: '188'
ht-degree: 0%

---

# ERRO: falha no aquecimento do Adobe Commerce na infraestrutura de nuvem

Este artigo fornece uma solução para quando o cache da página está sendo aquecido e falha com um erro:

*ERRO: Falha no aquecimento:`<website link>`*

## Produtos e versões afetados

* Adobe Commerce na infraestrutura em nuvem, todas as [versões com suporte](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Problema

Falha no aquecimento de cache.

<u>Etapas a serem reproduzidas</u>:

Iniciar operações de aquecimento do cache.

<u>Resultado esperado</u>:

Páginas ou todo o site é carregado.

<u>Resultado real</u>:

O site não está disponível ou o tempo de resposta é muito alto. *ERRO: Falha no aquecimento:`<website link>`*

## Causa

O aquecimento de cache não funciona com o controle de acesso HTTP ativado.

## Solução

Verifique se o controle de acesso está habilitado: vá para a ramificação/ambiente específico, clique no ícone **Configurações** e verifique a configuração **Controle de acesso HTTP** - o aquecimento do cache não pode ocorrer neste cenário e o controle de acesso deve ser desabilitado.

## Leitura relacionada

* [Guia do Usuário do Adobe Commerce > Cache de Página Inteira](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/cache-management#full-page-caching) em nosso guia do usuário.
* [Aquecimento de cache e site não disponível no Adobe Commerce](/help/troubleshooting/miscellaneous/cache-warming-up-and-site-unavailable-on-magento.md) em nossa base de dados de conhecimento de suporte.
