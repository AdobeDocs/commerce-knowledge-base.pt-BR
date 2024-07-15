---
title: Ex-membros da equipe recebem emails de notificação na nuvem do Adobe Commerce
description: Este artigo fornece uma solução para o Adobe Commerce em emails de notificação da infraestrutura em nuvem enviados para ex-membros da equipe.
exl-id: b2535f66-8aec-4ddf-9a69-60879a0a1939
feature: Cloud, Communications, Paas
role: Developer
source-git-commit: 0017d43e221ef3023630f714c34aa65b368e214f
workflow-type: tm+mt
source-wordcount: '244'
ht-degree: 0%

---

# Ex-membros da equipe recebem emails de notificação na nuvem do Adobe Commerce

Este artigo fornece uma solução para remover usuários da lista de destinatários de emails de notificação que são:
* Ex-membros da equipe que não estão mais associados ao seu projeto.
* Membros atuais da equipe que não devem receber as notificações.

## Problema

Um aviso de interrupção detectada ou problema importante relacionado ao projeto/ambiente de nuvem foi enviado à sua equipe. Isso inclui membros que não podem mais ser associados ao seu projeto, como desenvolvedores externos/de agências ou integradores de sistemas. Você deseja que esses usuários parem de receber notificações.

## Solução

Há duas maneiras de interromper as notificações removendo o(s) usuário(s) do projeto:

* Método 1: uso da nuvem [!DNL Project URL]. Consulte [Gerenciar o acesso do usuário](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html) no guia de infraestrutura do Commerce na nuvem para ver as etapas.
* Método 2: usar a magento-cloud [!DNL CLI]. Consulte [Gerenciar usuários com o  [!DNL CLI]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html#manage-users-with-the-cli) no guia de infraestrutura do Commerce na nuvem para ver as etapas.

Se isso já tiver sido feito e, ainda assim, as notificações por email continuarem a incluir esses usuários, envie um tíquete de suporte para solicitar que eles sejam removidos da configuração *[!UICONTROL Always CC]* na conta.

## Leitura relacionada

* [Exiba a função de projeto de um usuário](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html#view-a-user’s-project-role) no guia da infraestrutura do Commerce na nuvem.
* [Como incluir um membro da equipe nas notificações de suporte](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-include-a-team-member-in-support-notifications.html) na base de conhecimento da Commerce.
