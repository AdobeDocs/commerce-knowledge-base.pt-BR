---
title: Como atualizar o perfil da conta na nuvem
description: Este artigo fornece etapas para modificar o perfil na conta da nuvem.
feature: Cloud, Support
role: Admin, Developer
exl-id: b0c9dbcf-9745-494d-a662-80c5c6378068
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 5a951749-fac9-5bc7-9a98-ebe4ff066437
    internal-label: Cloud
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
subfeature_v2:
  - id: a59f76dc-e003-5617-951e-dffa5bd3de81
    internal-label: Support
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '256'
ht-degree: 1%
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

Consulte: [https://experienceleague.adobe.com/docs/commerce-admin/start/commerce-account/commerce-account-transfer.html?lang=pt-BR](https://experienceleague.adobe.com/docs/commerce-admin/start/commerce-account/commerce-account-transfer.html?lang=pt-BR)
