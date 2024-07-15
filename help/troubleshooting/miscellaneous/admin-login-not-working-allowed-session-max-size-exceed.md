---
title: O logon '[!DNL Admin] não está funcionando - tamanho máximo de sessão permitido excedido'
description: Resolva o problema ao tentar fazer logon no painel  [!DNL Admin] e o formulário for atualizado e você não conseguir fazer logon.
exl-id: 12789df0-6130-4e60-a92a-68ed329bd7fd
source-git-commit: 8718148f6d9a40c9a71484a7fbc818a626e825e1
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 0%

---

# O login do [!DNL Admin] não está funcionando - tamanho máximo de sessão permitido excedido

Este artigo fornece uma correção para quando você tenta fazer logon no painel do [!DNL Admin], mas o formulário é atualizado e você não consegue fazer logon. Isso ocorre porque o Tamanho da Sessão [!DNL Admin] foi excedido.

## Versões afetadas

* Adobe Commerce local, [todas as versões com suporte](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)
* Adobe Commerce na infraestrutura em nuvem, [todas as versões com suporte](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## Problema

É impossível fazer logon no [!DNL Admin], pois o formulário continua sendo recarregado.

## Causa

O tamanho máximo de sessão permitido foi excedido.

## Solução

Verifique se há erros como estes no arquivo `var/log/support_report.log`:

*[2023-07-13T04:26:09.792060+00:00] report.WARNING: o tamanho da sessão de 260572 excedeu o tamanho máximo de sessão permitido de 256000. [] []
[2023-07-13T04:26:17.056714+00:00] report.WARNING: o tamanho da sessão de 260570 excedeu o tamanho máximo de sessão permitido de 256000. [][]*

Se você vir esses erros, a solução será:

<u>Adobe Commerce local</u>:
1. Aumente o valor **[!UICONTROL Max Session Size in Admin]** da configuração de back-end. Para fazer isso, vá para **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Security]** > **[!UICONTROL Max Session Size in Admin]**.
1. Defina o valor como *500000* ou superior. Dependendo do tamanho máximo existente relatado no erro, você também pode definir o valor como *0*, o que removerá o limite de tamanho da sessão.

<u>Adobe Commerce na infraestrutura em nuvem</u>:

(Essa configuração só é acessível no [!DNL Admin] quando o modo de implantação/operação é padrão ou de desenvolvedor. No entanto, somente o modo de implantação de Produção é permitido no ambiente de Nuvem.)

Para aumentar esse valor, execute este comando no terminal (SSH):

```ssh
bin/magento config:set system/security/max_session_size_admin 500000
```

Você pode definir como maior que *500000*, dependendo do tamanho máximo existente relatado no erro, e também pode definir o valor como *0* para remover o limite de tamanho da sessão.

## Leitura relacionada

* [Tamanho da sessão](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/security-session-management#admin-sessions) no Guia de Sistemas de Administração.
* [Modo de operação](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/set-mode) no Guia de Configuração.
* [Conexões seguras](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/secure-connections) no Guia de Infraestrutura do Commerce na Nuvem.
