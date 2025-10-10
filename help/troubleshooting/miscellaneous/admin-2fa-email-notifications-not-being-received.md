---
title: Notificações por email de administrador 2FA não recebidas
description: Este artigo fornece solução de problemas quando você não está recebendo o email com as instruções de conclusão da configuração depois de configurar a Autenticação de dois fatores (2FA) para melhorar a segurança de acesso do administrador no Adobe Commerce na infraestrutura em nuvem.
exl-id: 7ab6b2b4-6aca-4323-a45b-2b4e52955160
feature: Admin Workspace, Communications
role: Developer
source-git-commit: 9eaea028886e74fc06c9516801919cd7f650f98c
workflow-type: tm+mt
source-wordcount: '449'
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

Verifique se há emails na pasta Spam.

Se o e-mail apareceu na pasta Spam, a autenticação de e-mail do seu domínio pode não estar totalmente configurada para entrega de saída via SendGrid.

Se você estiver usando o serviço SendGrid gerenciado pelo Adobe:

[Envie um tíquete de suporte](https://experienceleague.adobe.com/home?lang=pt-BR&support-tab=home#support) solicitando que o seu domínio de envio seja autenticado (às vezes chamado de *com rótulo branco*) com SendGrid.
Esse processo envolve adicionar registros DNS (DKIM e SPF) para autorizar o SendGrid a enviar emails em nome de seu domínio, o que aumenta a probabilidade de seus emails serem entregues na caixa de entrada em vez da pasta Spam.

Se você estiver usando sua própria conta do SendGrid:

Você é responsável por gerenciar as configurações de autenticação de domínio diretamente no painel de conta do SendGrid. Consulte [Como Configurar a Autenticação de Domínio](https://www.twilio.com/docs/sendgrid/ui/account-and-settings/how-to-set-up-domain-authentication) na documentação do SendGrid para obter detalhes.

>[!NOTE]
>
>Alguns clientes podem optar por usar um serviço SendGrid provisionado separadamente para obter controle total sobre a capacidade de entrega e a conformidade de emails (por exemplo, requisitos da HIPAA). Siga as etapas corretas de solução de problemas de acordo com o tipo de serviço SendGrid (gerenciado pela Adobe versus gerenciado automaticamente) que você está usando.


## Leitura relacionada

* [SendGrid](https://experienceleague.adobe.com/pt-br/docs/commerce-cloud-service/user-guide/project/sendgrid) em nossa documentação do desenvolvedor.
