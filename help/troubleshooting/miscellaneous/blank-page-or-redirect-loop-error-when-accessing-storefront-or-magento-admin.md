---
title: Página em branco ou erro de loop de redirecionamento ao acessar a loja ou o administrador do Commerce
description: Este artigo fornece uma solução para o problema quando você acessa a loja ou o backend da Adobe Commerce e obtém uma página em branco ou um loop de redirecionamento.
exl-id: 65869de2-1939-481b-844b-69122345b407
feature: Admin Workspace, Cache, Storefront
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 0%

---

# Página em branco ou erro de loop de redirecionamento ao acessar a loja ou o administrador do Commerce

Este artigo fornece uma solução para o problema quando você acessa a loja ou o backend da Adobe Commerce e obtém uma página em branco ou um loop de redirecionamento.

## Produtos e versões afetados

* Adobe Commerce na infraestrutura em nuvem, todas as versões
* Adobe Commerce no local, todas as versões
* Magento Open Source, todas as versões

## Problema

<u>Etapas a serem reproduzidas</u>

Abra uma vitrine ou uma página de Administrador.

<u>Resultado esperado</u>

A página é aberta.

<u>Resultado real</u>

A página está em branco ou exibe o *&quot;Esta página da Web tem um loop de redirecionamento&quot;* mensagem de erro.

## Causa

Uma das razões mais prováveis para o problema é que o Adobe Commerce está definido para redirecionar de URL não seguro para URL seguro, mas um URL não seguro é fornecido como o valor da configuração de URL seguro.

Para corrigir o problema, é necessário corrigir o valor do link seguro.

## Solução

Para verificar se essa é a causa do problema, execute as seguintes etapas:

1. Verifique a `web/secure/enable_upgrade_insecure` , `web/secure/use_in_adminhtml` (se você tiver o problema de redirecionamento em branco/loop no Admin) ou `web/secure/use_in_frontend` (se você tiver o problema de redirecionamento em branco/loop na loja) na variável `'core_config_data'` Tabela DB.
   * Se `web/secure/enable_upgrade_insecure` for definido como &quot;1&quot;, o Adobe Commerce será configurado para adicionar o cabeçalho de resposta `Content-Security-Policy: upgrade-insecure-requests`, instruindo os navegadores a usar HTTPS, redirecionando todas as consultas que vêm via HTTP para HTTPS, para Admin e loja.
   * Se `web/secure/use_in_adminhtml` for definido como &quot;1&quot;, o Adobe Commerce retornará redirecionamentos HTTPS para todas as solicitações HTTP das páginas de Administrador.
   * Se `web/secure/use_in_frontend` for definido como &quot;1&quot;, o Adobe Commerce retornará redirecionamentos HTTPS para todas as solicitações HTTP das páginas iniciais da loja.
1. Verifique a `web/secure/base_url` e `web/unsecure/base_url` valores no `'core_config_data'` tabela. Se ambos começarem com    `http`, é necessário corrigir o valor &quot;seguro&quot;.

Correção do problema:

1. Defina o valor começando com `https` para `web/secure/base_url.`
1. Para que as alterações sejam aplicadas, limpe o cache de configuração executando o seguinte comando:

   ```bash
   php <your_magento_install_dir>/bin/magento cache:clean config
   ```
