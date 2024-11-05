---
title: 'Redirecionar de volta para o formulário de logon do [!UICONTROL Commerce Admin] com o erro "Sua sessão atual expirou"'
description: '''Este artigo fornece as soluções possíveis para o problema de logon do [!UICONTROL Commerce Admin], para o qual você é redirecionado de volta ao formulário de logon com a seguinte mensagem de erro: *"Sua sessão atual expirou"*. As soluções incluem a verificação de problemas de configuração de tempo do servidor e a alteração das configurações de armazenamento da sessão."'
exl-id: 29df2ed2-ff4a-4f1a-bdb7-1160416cda00
feature: Admin Workspace
role: Developer
source-git-commit: 3f205b1d755bda7056f47bf1e1d036feb47ebadd
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---

# Redirecione de volta para o formulário de logon do [!UICONTROL Commerce Admin] com o erro &quot;Sua sessão atual expirou&quot;

Este artigo fornece as soluções possíveis para o problema de logon do [!UICONTROL Commerce Admin], para o qual você é redirecionado de volta ao formulário de logon com a seguinte mensagem de erro: *&quot;Sua sessão atual expirou&quot;*. As soluções incluem a verificação de problemas de configuração de tempo do servidor e a alteração das configurações de armazenamento de sessão.

## Edições e versões afetadas:

Todas as versões e edições do Adobe Commerce

## Problema

<u>Etapas a serem reproduzidas</u>:

1. Vá para a página **[!UICONTROL Commerce Admin]**.
1. Insira suas credenciais e clique em **Entrar**.

<u>Resultado esperado</u>:

Você fez logon no [!UICONTROL Commerce Admin].

<u>Resultado real</u>:

Você será redirecionado de volta ao formulário de logon, com a seguinte mensagem de erro exibida: *&quot;Sua sessão atual expirou&quot;*.

## Causa

Pode haver dois motivos possíveis para o problema:

* um problema com as configurações de hora do servidor
* um problema com o armazenamento da sessão

Verifique a seção a seguir para obter soluções.

## Solução

### Verificar problemas de configurações de tempo do servidor

Verifique o registro de sessão criado na tabela `admin_user_session`. Se os valores de `created_at` e/ou `updated_at` estiverem incorretos, isso poderá ser causado pelo problema com as configurações de hora do servidor. Peça ao administrador do sistema do servidor para verificar isso. Observe que o horário em DB é definido como UTC por padrão.

### Alterar o armazenamento da sessão

Tente alterar o armazenamento da sessão. Use as informações do artigo [Como localizar seus arquivos de sessão](https://devdocs.magento.com/guides/v2.3/config-guide/sessions.html) na documentação do desenvolvedor para descobrir onde sua sessão está armazenada e alterá-lo editando o arquivo `app/etc/env.php`.

Por exemplo, para iniciar o armazenamento da sessão no sistema de arquivos, altere a seção `'session'` da seguinte maneira:

```php
....
'session' =>
    array (
      'save' => 'files',
),
....
```

Execute o comando `bin/magento app:config:import` para importar dados de configuração.


## Leitura relacionada

* [Importe dados de arquivos de configuração](https://devdocs.magento.com/guides/v2.3/config-guide/cli/config-cli-subcommands-config-mgmt-import.html) em nossa documentação do desenvolvedor
* [Configurar [!DNL Redis]](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cache/redis/config-redis) na documentação do desenvolvedor
* [Redirecione de volta para o formulário de logon [!UICONTROL Commerce Admin] com o erro &quot;Sua conta está temporariamente desabilitada&quot;](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/redirect-back-to-the-admin-login-form-with-your-account-is-temporarily-disabled-error) em nossa base de dados de conhecimento de suporte
* [Redirecionar de volta para o formulário de logon sem erro ao tentar fazer logon no [!UICONTROL Commerce Admin]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/login-redirect-when-trying-to-login-to-magento-admin) em nossa base de dados de conhecimento de suporte
* [Práticas recomendadas para modificar tabelas de banco de dados](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) no Manual de implementação do Commerce

