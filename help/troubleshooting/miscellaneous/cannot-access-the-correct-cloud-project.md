---
title: Não é possível acessar a conta/projeto correto do Adobe Commerce ou o projeto está ausente em sua conta
description: Este artigo fornece uma correção para o problema que ocorria quando não era possível acessar o projeto correto do Cloud Adobe Commerce quando havia alterações nas propriedades ou nos endereços de email.
exl-id: 165b9a18-6e84-4f0f-b377-a07152d55c9e
hide: true
hidefromtoc: true
feature: Cloud, Paas
role: Developer
source-git-commit: 423a392eb32df69c38b84081ac2ed17ae1efdc7b
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# Não é possível acessar a conta/projeto de nuvem correto ou o projeto está ausente em sua conta

Este artigo fornece uma correção para os seguintes problemas depois que uma alteração é feita na propriedade da conta ou nos endereços de email associados:

1. Você não pode acessar o(s) projeto(s) correto(s) do Cloud Adobe Commerce.
1. Nenhum projeto do Cloud Adobe Commerce é mostrado na sua conta em [accounts.magento.cloud/user](https://accounts.magento.cloud/user).
1. Você está vendo os detalhes de outra conta (ou seja, o proprietário da conta anterior) em [accounts.magento.cloud/user](https://accounts.magento.cloud/user).

## Problema

Você não pode acessar o projeto correto do Cloud Adobe Commerce quando há alterações nas propriedades ou alterações nos endereços de email.

## Produtos e versões afetados

* Adobe Commerce na infraestrutura em nuvem, [todas as versões compatíveis](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## Causa

Normalmente, esse problema ocorre quando o logon único (SSO) do proprietário do projeto anterior ainda está integrado ao Adobe.com após:

1. A propriedade do projeto na nuvem foi transferida para você (o usuário) e você vê a conta do proprietário original do projeto. Clique aqui para o [solução](#solution-for-cause-one-and-two).

   OU

1. Você (o usuário) foi movido para uma empresa diferente, acompanhado por uma alteração no endereço de email e nos projetos aos quais você tem acesso. Você vê os projetos aos quais recebeu acesso na sua função/empresa anterior. Clique aqui para o [solução](#solution-for-cause-one-and-two).

   OU

1. Você alterou seu endereço de email em https://account.adobe.com para outro endereço de email que não está atualmente associado a um projeto na nuvem. Clique aqui para o [solução](#solution-for-cause-three).

## Solução para causa um e dois {#solution-for-cause-one-and-two}

A solução para quando o problema for causado por um e dois é desconectar a integração de logon único com Adobe.com. Siga as etapas abaixo para desconectar:

1. Em https://accounts.magento.cloud/user, expanda a variável **[!UICONTROL Single Sign-On]** seção. Clique em **[!UICONTROL Disconnect from Adobe.com]**, para desconectar.

   ![single-sign-on-adobe-connect](assets/sso-adobe-disconnect.png)

1. Clique em **[!UICONTROL Disconnect]**.

   ![adobe-disconnect](assets/adobe-disconnect.png)

1. Faça logout.
1. Clique no link **[!UICONTROL Adobe.com]** botão.

   ![Magento.com](assets/adobe-welcome-login.png)

1. Agora você pode ver a conta correta e acessar o projeto de nuvem correto.

## Solução da causa três {#solution-for-cause-three}

Se o problema tiver sido causado pela causa três, peça a um superusuário existente no projeto para adicionar seu novo endereço de email ao projeto. Para obter mais informações, consulte [Gerenciar acesso do usuário](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html).
