---
title: Alterar a senha do administrador no Adobe Commerce na infraestrutura em nuvem
description: '![login_panel_s.png](assets/login_panel_s.png)'
exl-id: 1b6e867e-d314-4e7b-be95-d699e6749896
feature: Admin Workspace, Cloud
source-git-commit: 7dc84525aef4d59346bb9bc980a7ed9b7f6612cf
workflow-type: tm+mt
source-wordcount: '160'
ht-degree: 0%

---

# Alterar a senha do administrador no Adobe Commerce na infraestrutura em nuvem

## Método 1: Esqueceu sua senha (redefinir por email)

![login_panel_s.png](assets/login_panel_s.png)

Leia as etapas no [Redefina sua seção de senha do Logon do administrador](https://experienceleague.adobe.com/docs/commerce-admin/start/admin/admin-signin.html#admin-sign-in) em nosso guia do usuário.

Abaixo estão as notas de uso críticas.

### Ativar emails de saída

Antes de usar o **Esqueceu sua senha** formulário, [ativar emails de saída](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/outgoing-emails.html) usando o [Cloud Console](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html).

### Verificar a pasta Lixo Eletrônico

Se não conseguir encontrar a mensagem com um link Redefinir senha, verifique *Lixo Eletrônico* pasta. O nome do email é *Confirmação de redefinição de senha para o nome de usuário administrador*.

## Método 2: adicionar um novo usuário administrador

Se não conseguir restaurar ou redefinir a senha do usuário existente, você poderá criar um novo usuário administrador e definir uma senha para esse usuário. Para fazer isso, siga estas etapas:

1. Uso [SSH para fazer logon no ambiente remoto](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html).
1. Execute o seguinte comando: `bin/magento admin:user:create   --admin-user=%user_name% --admin-password=%your_password% --admin-email=%your_email% --admin-firstname=%admin_user_first_name% --admin-lastname=%admin_user_last_name%`
