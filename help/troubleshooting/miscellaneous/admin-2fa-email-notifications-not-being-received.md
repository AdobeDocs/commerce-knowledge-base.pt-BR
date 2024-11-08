---
title: Notificações por email de administrador 2FA não recebidas
description: Este artigo fornece solução de problemas quando você não está recebendo o email com as instruções de conclusão da configuração depois de configurar a Autenticação de dois fatores (2FA) para melhorar a segurança de acesso do administrador no Adobe Commerce na infraestrutura em nuvem.
exl-id: 7ab6b2b4-6aca-4323-a45b-2b4e52955160
feature: Admin Workspace, Communications
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '300'
ht-degree: 0%

---

# Notificações por email de administrador 2FA não recebidas


## Produtos e versões afetados

* Adobe Commerce na infraestrutura em nuvem, todas as versões

## Problema

Você configurou a Autenticação de dois fatores para melhorar a segurança de acesso do Administrador, mas não está recebendo o email com as instruções sobre como concluir a configuração.

## Causa

Se você não tiver configurado o e-mail do remetente corretamente ou se o domínio não tiver sido rotulado com um rótulo branco no SendGrid, o e-mail provavelmente terá chegado à pasta de spam.

## Solução de problemas

### Etapa 1: verifique sua pasta de spam

1. Se o e-mail não tiver sido exibido na sua pasta de spam, execute esta consulta Mysql para verificar se os endereços de e-mail foram configurados:

   ```sql
   select * from core_config_data where path like '%trans_email%';
   ```

   * Se não retornar nenhum resultado, significa que o endereço do Remetente não foi configurado.
Como você não tem acesso ao administrador, será necessário inserir a configuração no banco de dados. Conecte o endereço de email apropriado e execute a instrução MySQL:

   ```
   insert into core_config_data (scope,scope_id,path,value) values ('default',0,'trans_email/ident_general/email', your-email@here.com)
   ```

   * Se retornar um resultado, prossiga para **Etapa 2**.

1. Se o e-mail apareceu na pasta Spam, clique no link do e-mail. Se o link já tiver expirado, tente fazer logon novamente para repetir o processo.
1. Depois de obter acesso, vá para **Lojas** > **Configuração** > **Geral** > **Armazenar Endereços de Email** e configure os endereços de email.

### Etapa 2: se/uma vez que os endereços de email tenham sido configurados corretamente, SSH no ambiente e execute este comando:

```php
php -r "mail(<your email address>,<subject>,<content>,'To: <sender email>');"
```

Verifique se há emails na pasta Spam. Se o email apareceu lá, [envie um tíquete de suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#login) para solicitar que o domínio seja rotulado como branco no SendGrid.

## Leitura relacionada

* [SendGrid](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/project/sendgrid) em nossa documentação do desenvolvedor.
