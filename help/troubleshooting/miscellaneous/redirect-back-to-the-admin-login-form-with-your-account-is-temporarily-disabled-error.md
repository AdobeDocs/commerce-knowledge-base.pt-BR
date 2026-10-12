---
title: Redirecione de volta para o formulário de logon do [!UICONTROL Commerce Admin] com o erro "Sua conta está temporariamente desabilitada"
description: 'Este artigo fornece as soluções possíveis para o problema de logon de administrador do Commerce, em que você é redirecionado de volta para o formulário de logon com a seguinte mensagem de erro: *"Sua conta está temporariamente desabilitada"*. A solução sugerida é verificar e corrigir as configurações do banco de dados do usuário administrador.'
exl-id: 1c7ffa1c-1fb1-4f69-9534-77d1e119318a
feature: Admin Workspace, Customer Service
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
  - id: da76473c-f99b-5ad0-9b14-896aed473f8a
    internal-label: Services
subfeature_v2:
  - id: bb2df8be-afdd-4818-b6b5-95ca1dd3bc3a
    internal-label: Admin workspace
  - id: deedbb4d-f1b7-58ea-a34a-de1f481f9d4c
    internal-label: Customer Service
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '256'
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
1. Use uma ferramenta de banco de dados como [[!DNL phpMyAdmin]](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/installation-guide/prerequisites/optional-software#phpmyadmin) ou acesse o BD manualmente a partir da linha de comando. Na tabela do banco de dados `admin_user`, para seu registro de usuário administrador, verifique se `is_active` está definido como &quot;`1`&quot; e `lock_expires` é `NULL`. Redefina esses valores, se necessário.

## Leitura relacionada

* [Práticas recomendadas para modificar tabelas de banco de dados](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) no Manual de implementação do Commerce
