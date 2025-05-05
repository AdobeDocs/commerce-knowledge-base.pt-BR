---
title: Redirecionamento de logon ao tentar fazer logon no Commerce Admin
description: Este artigo fornece as soluções possíveis para o problema de logon do Commerce Admin, em que você é redirecionado de volta para o formulário de logon ao tentar fazer logon no Admin e nenhuma mensagem de erro é exibida. Isso inclui a correção das configurações de fuso horário do servidor e a limpeza das configurações de cookies no Adobe Commerce.
exl-id: ff3114fd-8690-4983-8221-cf807f083b15
feature: Admin Workspace, Cache
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 0%

---

# Redirecionamento de logon ao tentar fazer logon no Commerce Admin

Este artigo fornece as soluções possíveis para o problema de logon do Commerce Admin, em que você é redirecionado de volta para o formulário de logon ao tentar fazer logon no Admin e nenhuma mensagem de erro é exibida. Isso inclui a correção das configurações de fuso horário do servidor e a limpeza das configurações de cookies no Adobe Commerce.

## Edições e versões afetadas:

Todas as versões e edições do Adobe Commerce.

## Problema

<u>Etapas a serem reproduzidas</u>:

1. Vá para a página de Administrador do Commerce.
1. Insira suas credenciais e clique em Fazer logon.

<u>Resultados esperados</u>:

Você faz logon no Commerce Admin.

<u>Resultados reais</u>:

Você será redirecionado de volta ao formulário de logon sem mensagens de erro.

## Causa

Há algumas razões possíveis para o problema:

* Fuso horário incorreto definido no nível do navegador (o que faz com que a sessão do administrador seja considerada expirada, mesmo que o tempo de vida real ainda não tenha expirado).
* Configurações de cookies incorretas, o que faz com que a sessão estabelecida não seja usada pelo Adobe Commerce.

Consulte os próximos parágrafos para obter soluções para cada caso.

## Soluções

### Problema relacionado ao tempo de vida da sessão do administrador

Tente usar um navegador diferente e aumente o tempo de vida da sessão do administrador se for inferior a uma hora.

Para aumentar o tempo de vida da sessão de administrador, siga estas etapas:

1. Criar um backup de banco de dados.
1. Use uma ferramenta de banco de dados como [phpMyAdmin](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/installation-guide/prerequisites/optional-software#phpmyadmin) ou acesse o BD manualmente a partir da linha de comando para executar a seguinte consulta SQL:

   ```sql
   UPDATE core_config_data SET value = 7200 WHERE path = 'admin/security/session_lifetime';
   ```

1. Limpe o cache de configuração executando o seguinte comando:

   ```bash
   php <your_magento_install_dir>/bin/magento cache:clean config
   ```

### Configurações de cookies incorretas

Para verificar os valores das configurações de cookies e limpá-los, siga estas etapas:

1. Criar um backup de banco de dados.
1. Use uma ferramenta de banco de dados como [phpMyAdmin](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/installation-guide/prerequisites/optional-software#phpmyadmin) ou acesse o BD manualmente a partir da linha de comando para executar a seguinte consulta SQL:

   ```sql
   SELECT * FROM core_config_data WHERE (path = "web/cookie/cookie_domain" OR path = "web/cookie/cookie_path");
   ```

1. Se as respostas dos valores não estiverem vazias, defina-as como NULL executando:

   ```sql
   UPDATE core_config_data SET value = NULL WHERE (path = "web/cookie/cookie_domain" OR path = "web/cookie/cookie_path");
   ```

1. Limpe o cache de configuração executando o seguinte comando:

   ```bash
   php <your_magento_install_dir>/bin/magento cache:clean config
   ```

## Artigos relacionados

* [Redirecione de volta para o formulário de logon do Administrador com o erro &quot;Sua conta está temporariamente desabilitada&quot;](/help/troubleshooting/miscellaneous/redirect-back-to-the-admin-login-form-with-your-account-is-temporarily-disabled-error.md) em nossa knowledge base de suporte.
* [Redirecione de volta para o formulário de logon do Administrador com o erro &quot;Sua sessão atual expirou&quot;](/help/troubleshooting/miscellaneous/redirect-back-to-the-admin-login-form-with-your-current-session-has-been-expired-error.md) em nossa base de dados de conhecimento de suporte.
