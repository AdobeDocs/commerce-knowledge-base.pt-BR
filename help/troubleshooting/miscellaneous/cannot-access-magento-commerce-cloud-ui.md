---
title: Não é possível acessar o Adobe Commerce na interface do usuário da infraestrutura em nuvem
description: Este artigo fornece soluções para o problema em que você não consegue fazer logon na interface do usuário da Adobe Commerce na infraestrutura em nuvem e recebe o "erro 403".
exl-id: 948e4acd-abd6-4562-b9c0-771a977188ba
feature: Cloud, Paas
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 5a951749-fac9-5bc7-9a98-ebe4ff066437
    internal-label: Cloud
  - id: 00451af3-7b97-5414-9992-3a6c269e413f
    internal-label: Paas
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '332'
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
1. Se o erro persistir, [envie um tíquete de suporte](https://experienceleague.adobe.com/pt-br/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#submit-ticket).
