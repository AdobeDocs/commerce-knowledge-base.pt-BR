---
title: Alterar a senha do administrador no Adobe Commerce na infraestrutura em nuvem
description: '![login_panel_s.png](assets/login_panel_s.png)'
exl-id: 1b6e867e-d314-4e7b-be95-d699e6749896
feature: Admin Workspace, Cloud
source-git-commit: 44238f6d57458028cb1e2612d45e1e12b3f39916
workflow-type: tm+mt
source-wordcount: '217'
ht-degree: 0%

---

# Alterar a senha do administrador no Adobe Commerce na infraestrutura em nuvem

## Método 1: Esqueceu sua senha (redefinir por email)

![login_panel_s.png](assets/login_panel_s.png)

Leia as etapas na seção [Redefinir sua senha de Entrada de Administrador](https://experienceleague.adobe.com/docs/commerce-admin/start/admin/admin-signin.html?lang=pt-BR#admin-sign-in) em nosso guia do usuário.

Abaixo estão as notas de uso críticas.

### Ativar emails de saída

Antes de usar o formulário **Esqueceu sua senha**, [habilite os emails de saída](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/outgoing-emails.html?lang=pt-BR) usando o [Cloud Console](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html?lang=pt-BR). Isso se aplica somente a ambientes de integração e projetos de sandbox.

Se os emails de saída estiverem realmente desabilitados na Produção ou Preparo Pro - o que significa que o email não foi selecionado pelo SendGrid - você poderá verificar isso marcando [Habilitar emails no Cloud Console](https://experienceleague.adobe.com/pt-br/docs/commerce-on-cloud/user-guide/project/outgoing-emails#enable-emails-in-the-cli). Se o problema persistir, você pode enviar um [Tíquete de suporte](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide) do Adobe.

### Verificar a pasta Lixo Eletrônico

Se não conseguir localizar a mensagem com um link Redefinir Senha, verifique a pasta *Lixo Eletrônico*. O nome do email é *Confirmação de Redefinição de Senha para o Nome de Usuário Administrador*.

## Método 2: adicionar um novo usuário administrador

Se não conseguir restaurar ou redefinir a senha do usuário existente, você poderá criar um novo usuário administrador e definir uma senha para esse usuário. Para fazer isso, siga estas etapas:

1. Use o [SSH para fazer logon no ambiente remoto](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html?lang=pt-BR).
1. Execute o seguinte comando: `bin/magento admin:user:create   --admin-user=%user_name% --admin-password=%your_password% --admin-email=%your_email% --admin-firstname=%admin_user_first_name% --admin-lastname=%admin_user_last_name%`
