---
title: Como incluir um membro da equipe nas notificações de suporte
description: Este artigo fornece uma explicação de como incluir um membro da equipe nas notificações de suporte.
feature: Cloud, Support, Admin Workspace
role: Admin, Developer
exl-id: 63ea3f60-a509-447c-ac3d-bb2133141c80
source-git-commit: 1c568d75534bbfe322d9f980b40c5dd64fc5b7a2
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 0%

---

# Como incluir um membro da equipe nas notificações de suporte

Este artigo fornece uma explicação de como incluir um membro da equipe para receber automaticamente atualizações de suporte por notificações por email.

## Produtos e versões afetados

* Adobe Commerce na infraestrutura em nuvem, tudo [versões compatíveis](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf).

## Causa

* O membro da equipe não foi adicionado ao [!DNL cloud project] com os privilégios necessários.
* O membro da equipe não tem uma conta de suporte.

## Solução

1. Vá para a **[!DNL Cloud Project URL]** (Exemplo: `https://us-3.magento.cloud/projects/xxxxxx/edit`).
1. Verificar se o membro da equipe foi adicionado ao projeto e se é um [!DNL Super User].

Se não exigirem [!DNL cloud project] acesso, enviar um [Solicitação de suporte no Adobe Commerce Support Center](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) para CC automaticamente: em todos os tickets, e também forneça seus **[!DNL MAGE ID]** (se disponível).

Se não tiverem sido adicionados ao projeto, será necessário adicioná-los como [!DNL Super User] e conceder [!DNL Shared Access]:

* [Gerenciar acesso do usuário](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html) em nosso guia do usuário.
* [Não foi possível adicionar o usuário ao projeto na nuvem do Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/unable-add-user-adobe-commerce-cloud-project.html) em nossa Base de conhecimento Commerce.
* [Guia do usuário da Central de ajuda do Adobe Commerce: Acesso compartilhado](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#shared-access) em nossa Base de conhecimento Commerce.

Se tiverem sido adicionados ao [!DNL cloud project], mas não têm o [!DNL Super User role], atualizam os seus [!DNL role] em conformidade com [Gerenciar acesso do usuário](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html).

## Leitura relacionada

[Ex-membros da equipe recebem emails de notificação na nuvem do Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/former-teammembers-receive-cloud-notification-emails.html)
