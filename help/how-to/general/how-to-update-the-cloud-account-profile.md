---
title: Como atualizar o perfil da conta na nuvem
description: Este artigo fornece etapas para modificar o perfil na conta da nuvem.
feature: Cloud, Support
role: Admin, Developer
exl-id: b0c9dbcf-9745-494d-a662-80c5c6378068
source-git-commit: bc8dbb1b43c3f2ad8f2ac214fd303f6a4d3e3412
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 0%

---

# Como atualizar o perfil da conta na nuvem

Este artigo fornece etapas sobre como modificar o perfil na conta da nuvem.

## Solução

Ao modificar um perfil na conta da nuvem, os seguintes campos podem ser modificados:

1. [!UICONTROL First name]
1. [!UICONTROL Last name]
1. [!UICONTROL Username]

   >[!NOTE]
   >
   >A atualização do nome de usuário do Cloud Console altera a URL do projeto de `https://console.adobecommerce.com <old-username>/<project-id>` para `https://console.adobecommerce.com/<new-username>/<project-id>`.
   >
   >Após a atualização, os links que usam o URL antigo não funcionarão mais. Os membros da equipe devem atualizar marcadores salvos, documentação interna e qualquer automação para usar o novo URL.
   >
   >Essa alteração se aplica somente ao novo URL do Cloud Console. A URL do projeto herdado (`https://<region>.magento.cloud/projects/<project-id>`) não usa o nome de usuário e continua a funcionar sem alteração.

Para modificar esses campos, siga estas etapas:

1. Acesse sua conta em [logon de conta da Adobe](https://accounts.magento.cloud).
1. Clique na guia **[!UICONTROL Account Settings]**.
1. Marque a caixa de seleção *criar nova senha*.
1. Faça as alterações necessárias e clique em *salvar*.

>[!NOTE]
>
>Sua senha não será alterada.

## O que não pode ser modificado?

1. **[!UICONTROL Password]**:
Para alterar sua senha, visite [Adobe password reset](https://account.adobe.com/), pois este perfil está vinculado à sua conta/endereço de email.

1. **[!UICONTROL Email Address]**:
A modificação desse campo depende de suas circunstâncias individuais.

Se precisar transferir a propriedade da conta atual para um novo proprietário ou um endereço de email diferente, será necessário atualizar o email do usuário principal associado à conta.

Consulte: [https://experienceleague.adobe.com/docs/commerce-admin/start/commerce-account/commerce-account-transfer.html?lang=en](https://experienceleague.adobe.com/docs/commerce-admin/start/commerce-account/commerce-account-transfer.html?lang=en)
