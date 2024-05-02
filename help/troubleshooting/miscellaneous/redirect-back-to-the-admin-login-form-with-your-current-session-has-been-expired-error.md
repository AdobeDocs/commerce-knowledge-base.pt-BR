---
title: Redirecione de volta para o formulário de logon do Administrador do Commerce com o erro "Sua sessão atual expirou"
description: '''Este artigo fornece as soluções possíveis para o problema de logon do Commerce Admin, em que você é redirecionado de volta ao formulário de logon com a seguinte mensagem de erro: *"Sua sessão atual expirou"*. As soluções incluem a verificação de problemas de configuração de tempo do servidor e a alteração das configurações de armazenamento da sessão."'
exl-id: 29df2ed2-ff4a-4f1a-bdb7-1160416cda00
feature: Admin Workspace
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# Redirecione de volta para o formulário de logon do Administrador do Commerce com o erro &quot;Sua sessão atual expirou&quot;

Este artigo fornece as soluções possíveis para o problema de logon de administrador do Commerce, em que você é redirecionado de volta para o formulário de logon com a seguinte mensagem de erro: *&quot;Sua sessão atual expirou&quot;*. As soluções incluem a verificação de problemas de configuração de tempo do servidor e a alteração das configurações de armazenamento de sessão.

## Edições e versões afetadas:

Todas as versões e edições do Adobe Commerce

## Problema

<u>Etapas a serem reproduzidas</u>:

1. Acesse a página de Administrador do Commerce.
1. Insira suas credenciais e clique em Fazer logon.

<u>Resultado esperado</u>:

Você faz logon no Commerce Admin.

<u>Resultado real</u>:

Você será redirecionado de volta ao formulário de logon, com a seguinte mensagem de erro exibida: *&quot;Sua sessão atual expirou&quot;*.

## Causa

Pode haver dois motivos possíveis para o problema:

* um problema com as configurações de hora do servidor
* um problema com o armazenamento da sessão

Verifique a seção a seguir para obter soluções.

## Solução

### Verificar problemas de configurações de tempo do servidor

Verifique o registro de sessão criado no `admin_user_session` tabela. Se os valores de `created_at` e/ou `updated_at` estiverem incorretos, isso pode ser causado pelo problema nas configurações de hora do servidor. Peça ao administrador do sistema do servidor para verificar isso. Observe que o horário em DB é definido como UTC por padrão.

### Alterar o armazenamento da sessão

Tente alterar o armazenamento da sessão. Use as informações do [Como localizar seus arquivos de sessão](https://devdocs.magento.com/guides/v2.3/config-guide/sessions.html) artigo em nossa documentação do desenvolvedor para descobrir onde sua sessão está armazenada e alterá-la editando o `app/etc/env.php` arquivo.

Por exemplo, para iniciar o armazenamento de uma sessão no sistema de arquivos, altere a variável `'session'` seção como segue:

```php
....
'session' =>
    array (
      'save' => 'files',
),
....
```

Execute o `bin/magento app:config:import` para importar dados de configuração.


## Leitura relacionada

* [Importar dados de arquivos de configuração](https://devdocs.magento.com/guides/v2.3/config-guide/cli/config-cli-subcommands-config-mgmt-import.html) na documentação do desenvolvedor
* [Configurar Redis](https://devdocs.magento.com/guides/v2.3/config-guide/redis/config-redis.html) na documentação do desenvolvedor
* [Redirecione de volta para o formulário de logon de administrador do Commerce com o erro &quot;Sua conta está temporariamente desativada&quot;](/help/troubleshooting/miscellaneous/redirect-back-to-the-admin-login-form-with-your-account-is-temporarily-disabled-error.md) em nossa base de conhecimento de suporte
* [Redirecionar de volta para o formulário de logon sem erro ao tentar fazer logon no administrador do Commerce](/help/troubleshooting/miscellaneous/login-redirect-when-trying-to-login-to-magento-admin.md) em nossa base de conhecimento de suporte
