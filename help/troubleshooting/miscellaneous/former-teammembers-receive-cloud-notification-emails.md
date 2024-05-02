---
title: Ex-membros da equipe recebem emails de notificação na nuvem do Adobe Commerce
description: Este artigo fornece uma solução para o Adobe Commerce em emails de notificação da infraestrutura em nuvem enviados para ex-membros da equipe.
exl-id: b2535f66-8aec-4ddf-9a69-60879a0a1939
feature: Cloud, Communications, Paas
role: Developer
source-git-commit: 075f295c5b600fcca9fbecc5aad20b0640d900f9
workflow-type: tm+mt
source-wordcount: '227'
ht-degree: 0%

---

# Ex-membros da equipe recebem emails de notificação na nuvem do Adobe Commerce

Este artigo fornece uma solução para o local em que os membros da equipe que não estão mais associados ao seu projeto continuarão a receber notificações.

## Problema

Um aviso de interrupção detectada ou problema importante relacionado ao projeto/ambiente de nuvem foi enviado à sua equipe. Isso inclui membros que não podem mais ser associados ao seu projeto, como desenvolvedores externos/de agências ou integradores de sistemas. Você deseja que esses usuários parem de receber notificações.

## Solução

Há duas maneiras de interromper as notificações removendo o(s) usuário(s) do projeto:

* Método 1: usar a nuvem [!DNL Project URL]. Consulte [Gerenciar acesso do usuário](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html) no guia Commerce na infraestrutura em nuvem para ver as etapas.
* Método 2: usar a magento-cloud [!DNL CLI]. Consulte [Gerenciar usuários com o [!DNL CLI]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html#manage-users-with-the-cli) no guia Commerce na infraestrutura em nuvem para ver as etapas.

Se isso já tiver sido feito e, ainda assim, as notificações por email continuarem a incluir esses usuários, envie um tíquete de suporte para solicitar que eles sejam removidos do *[!UICONTROL Always CC]* na conta.

## Leitura relacionada

* [Exibir a função de projeto de um usuário](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html#view-a-user’s-project-role) no guia Commerce on cloud infrastructure.
* [Como incluir um membro da equipe nas notificações de suporte](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-include-a-team-member-in-support-notifications.html) na Base de conhecimento do Commerce.
