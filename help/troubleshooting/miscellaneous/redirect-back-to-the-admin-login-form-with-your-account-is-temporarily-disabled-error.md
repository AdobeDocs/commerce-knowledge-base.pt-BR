---
title: Redirecione de volta para o formulário de logon do [!UICONTROL Commerce Admin] com o erro "Sua conta está temporariamente desabilitada"
description: 'Este artigo fornece as soluções possíveis para o problema de logon de administrador do Commerce, em que você é redirecionado de volta para o formulário de logon com a seguinte mensagem de erro: *"Sua conta está temporariamente desabilitada"*. A solução sugerida é verificar e corrigir as configurações do banco de dados do usuário administrador.'
exl-id: 1c7ffa1c-1fb1-4f69-9534-77d1e119318a
feature: Admin Workspace, Customer Service
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '240'
ht-degree: 0%

---

# Redirecione de volta para o formulário de logon do [!UICONTROL Commerce Admin] com o erro &quot;Sua conta está temporariamente desabilitada&quot;

Este artigo fornece as soluções possíveis para o problema de logon do [!UICONTROL Commerce Admin], para o qual você é redirecionado de volta ao formulário de logon com a seguinte mensagem de erro: *&quot;Sua conta está temporariamente desabilitada&quot;*. A solução sugerida é verificar e corrigir as configurações do banco de dados do usuário administrador.

## Edições e versões afetadas:

Todas as versões e edições do Adobe Commerce

## Problema

<u>Etapas a serem reproduzidas</u>:

1. Vá para a página **[!UICONTROL Commerce Admin]**.
1. Insira suas credenciais e clique em **Entrar**.

<u>Resultado esperado</u>:

Você fez logon no [!UICONTROL Commerce Admin].

<u>Resultado real</u>:

Você será redirecionado de volta ao formulário de logon, com a seguinte mensagem de erro exibida: *&quot;Sua conta está temporariamente desabilitada. Tente novamente mais tarde&quot;*.

## Solução

1. Criar um backup de banco de dados.
1. Use uma ferramenta de banco de dados como [[!DNL phpMyAdmin]](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/optional-software#phpmyadmin) ou acesse o BD manualmente a partir da linha de comando. Na tabela do banco de dados `admin_user`, para seu registro de usuário administrador, verifique se `is_active` está definido como &quot;`1`&quot; e `lock_expires` é `NULL`. Redefina esses valores, se necessário.

## Leitura relacionada

* [Redirecionar de volta para o formulário de logon sem erro ao tentar fazer logon no [!UICONTROL Commerce Admin]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/login-redirect-when-trying-to-login-to-magento-admin)
* [Práticas recomendadas para modificar tabelas de banco de dados](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) no Manual de implementação do Commerce
