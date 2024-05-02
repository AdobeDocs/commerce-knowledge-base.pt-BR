---
title: '[!DNL Admin] o login não está funcionando - o tamanho máximo permitido da sessão foi excedido'
description: Resolva o problema ao tentar fazer logon na sua [!DNL Admin] O painel e o formulário são atualizados e você não consegue fazer logon.
exl-id: 12789df0-6130-4e60-a92a-68ed329bd7fd
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '315'
ht-degree: 0%

---

# [!DNL Admin] o logon não está funcionando - tamanho máximo de sessão permitido excedido

Este artigo fornece uma correção para quando você tenta fazer logon na sua [!DNL Admin] mas o formulário será atualizado e você não poderá fazer logon. Isso ocorre porque a variável [!DNL Admin] O tamanho da sessão foi excedido.

## Versões afetadas

* Adobe Commerce no local, [todas as versões compatíveis](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)
* Adobe Commerce na infraestrutura em nuvem, [todas as versões compatíveis](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## Problema

É impossível fazer logon na [!DNL Admin], pois o formulário continua sendo recarregado.

## Causa

O tamanho máximo de sessão permitido foi excedido.

## Solução

Verifique a `var/log/support_report.log` arquivo para erros como estes:

*[2023-07-13T04:26:09.792060+00:00] report.WARNING: o tamanho da sessão de 260572 excedeu o tamanho máximo permitido de sessão de 256000. [] []
[2023-07-13T04:26:17.056714+00:00] report.WARNING: o tamanho da sessão de 260570 excedeu o tamanho máximo permitido de sessão de 256000. [][]*

Se você vir esses erros, a solução será:

<u>Adobe Commerce no local</u>:
1. Aumente o **[!UICONTROL Max Session Size in Admin]** valor da configuração de back-end. Para fazer isso, acesse **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Security]** > **[!UICONTROL Max Session Size in Admin]**.
1. Defina o valor como *500000* ou superior. Dependendo do tamanho máximo existente relatado no erro, também é possível definir o valor como *0* que removerá o limite de tamanho da sessão.

<u>Adobe Commerce na infraestrutura em nuvem</u>:

(Essa configuração só pode ser acessada no [!DNL Admin] quando o modo de implantação/operação for padrão ou de desenvolvedor. No entanto, somente o modo de implantação de Produção é permitido no ambiente de Nuvem.)

Para aumentar esse valor, execute este comando no terminal (SSH):

```ssh
bin/magento config:set system/security/max_session_size_admin 500000
```

Você pode definir como maior que *500000* dependendo do tamanho máximo existente relatado no erro, também é possível definir o valor como *0* para remover o limite de tamanho da sessão.

## Leitura relacionada

* [Tamanho da sessão](/docs/commerce-admin/systems/security/security-session-management.html?lang=en#admin-sessions) no Guia de sistemas de administração.
* [Modo de operação](/docs/commerce-operations/configuration-guide/cli/set-mode.html) no Guia de configuração.
* [Conexões seguras](/docs/commerce-cloud-service/user-guide/develop/secure-connections.html) no Guia de infraestrutura do Commerce na nuvem.
