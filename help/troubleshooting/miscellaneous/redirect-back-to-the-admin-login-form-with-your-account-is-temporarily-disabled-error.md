---
title: Redirecione de volta para o formulário de logon de administrador do Commerce com o erro "Sua conta está temporariamente desativada"
description: '''Este artigo fornece as soluções possíveis para o problema de logon de administrador do Commerce, em que você é redirecionado de volta ao formulário de logon com a seguinte mensagem de erro: *"Sua conta está temporariamente desabilitada"*. A solução sugerida é verificar e corrigir as configurações do banco de dados do usuário administrador."'
exl-id: 1c7ffa1c-1fb1-4f69-9534-77d1e119318a
feature: Admin Workspace, Customer Service
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '245'
ht-degree: 0%

---

# Redirecione de volta para o formulário de logon de administrador do Commerce com o erro &quot;Sua conta está temporariamente desativada&quot;

Este artigo fornece as soluções possíveis para o problema de logon de Administrador do Commerce, no qual você é redirecionado de volta ao formulário de logon com a seguinte mensagem de erro: *&quot;Sua conta está temporariamente desabilitada&quot;*. A solução sugerida é verificar e corrigir as configurações do banco de dados do usuário administrador.

## Edições e versões afetadas:

Todas as versões e edições do Adobe Commerce

## Problema

<u>Etapas a serem reproduzidas</u>:

1. Acesse a página de Administrador do Commerce.
1. Insira suas credenciais e clique em Fazer logon.

<u>Resultado esperado</u>:

Você faz logon no Commerce Admin.

<u>Resultado real</u>:

Você será redirecionado de volta ao formulário de logon, com a seguinte mensagem de erro exibida: *&quot;Sua conta está temporariamente desabilitada. Tente novamente mais tarde&quot;*.

## Solução

1. Criar um backup de banco de dados.
1. Use uma ferramenta de banco de dados, como o [phpMyAdmin](https://devdocs.magento.com/guides/v2.2/install-gde/prereq/optional.html#install-optional-phpmyadmin), ou acesse o BD manualmente a partir da linha de comando. Na tabela do banco de dados `admin_user`, para seu registro de usuário administrador, verifique se `is_active` está definido como &quot;`1`&quot; e `lock_expires` é `NULL`. Redefina esses valores, se necessário.

## Leitura relacionada em nossa base de conhecimento de suporte

* [Redirecionar de volta para o formulário de logon sem erro ao tentar fazer logon no administrador do Commerce](/help/troubleshooting/miscellaneous/login-redirect-when-trying-to-login-to-magento-admin.md)
