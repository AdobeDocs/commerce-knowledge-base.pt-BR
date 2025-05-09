---
title: Não é possível acessar o Adobe Commerce na interface do usuário da infraestrutura em nuvem
description: Este artigo fornece soluções para o problema em que você não consegue fazer logon na interface do usuário da Adobe Commerce na infraestrutura em nuvem e recebe o "erro 403".
exl-id: 948e4acd-abd6-4562-b9c0-771a977188ba
feature: Cloud, Paas
role: Developer
source-git-commit: 3d3d2da45d164efbbbaf8c878967caf83f845a59
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 0%

---

# Não é possível acessar o Adobe Commerce na interface do usuário da infraestrutura em nuvem

Este artigo fornece soluções para o problema em que você não pode fazer logon na interface do usuário do Adobe Commerce na infraestrutura de nuvem e receber o *erro 403*.

## Problema

Ao tentar fazer logon na Adobe Commerce pela primeira vez na interface do usuário da infraestrutura em nuvem, você recebe o erro *403: Acesso negado ao ambiente*. Esse erro pode ocorrer porque acessar o URL da nuvem pela primeira vez carrega a ramificação mestre e talvez você não tenha acesso a essa ramificação.

## Solução

Se você receber um erro 403 ao acessar o URL pela primeira vez, verifique se você tem uma função na ramificação mestre.

1. Сcontate o proprietário da licença ou um superusuário no projeto e verifique se ele forneceu acesso a você como um **usuário de nível de ambiente**, também descrito em [Projetos na nuvem > Gerenciar usuários no Cloud Console](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html?lang=pt-BR#manage-users-from-the-cloud-console) na documentação do desenvolvedor.

   Se você tiver apenas uma função aplicável em uma ramificação específica, será necessário acessar o URL dessa ramificação, por exemplo,
   `https://console.adobecommerce.com/<owner-name>/<project-id>/<branch-name>`

   Na próxima vez que você acessar o URL principal, ele assumirá como padrão o último ambiente visitado.

1. Se você ainda não conseguir fazer logon, сcontate o proprietário da licença ou um superusuário no projeto e verifique se ele forneceu acesso a você como um **usuário de nível de projeto**, conforme descrito em [Projetos na nuvem > Adicionar um usuário ao projeto](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html?lang=pt-BR#add-a-user-to-the-project) na documentação do desenvolvedor.
1. Se o erro persistir, [envie um tíquete de suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).
