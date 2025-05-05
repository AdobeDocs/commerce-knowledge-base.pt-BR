---
title: Não foi possível adicionar o usuário ao projeto na nuvem do Adobe Commerce
description: Este artigo fornece uma solução para quando não é possível adicionar um usuário a um projeto na nuvem do Adobe Commerce.
exl-id: 59940916-bf92-4e89-a6f9-bca87c54125c
feature: Cloud, Paas
role: Developer
source-git-commit: af74d944553c34da2ac8343695bca49f971bc4e5
workflow-type: tm+mt
source-wordcount: '308'
ht-degree: 0%

---

# Não foi possível adicionar o usuário ao projeto na nuvem do Adobe Commerce

Este artigo fornece uma solução para quando você está tentando adicionar um usuário a um projeto na nuvem, mas falha com um erro: *O usuário XXX não existe*.

## Produtos e versões afetados

* Adobe Commerce na infraestrutura em nuvem, [todas as versões com suporte](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Problema

Este artigo fornece uma solução para quando não é possível adicionar um usuário a um projeto na nuvem do Adobe Commerce.

## Causa

Esse é o comportamento esperado. A conta do usuário deve ser criada primeiro em https://accounts.magento.cloud e vinculada ao Adobe SSO para que seja adicionado como usuário ao projeto.

## Solução

1. Peça ao usuário para fazer logon em sua conta em https://accounts.magento.cloud (ele já deve ter se registrado para uma conta em adobe.com nesse endereço de email. Criar/ter uma conta em https://account.adobe.com não significa automaticamente que o usuário teria uma conta em https://accounts.magento.cloud)
Observação: se o usuário tiver uma conta no account.magento.com ou accounts.magento.cloud antes de agosto de 2022, talvez ele não tenha uma conta no/no adobe.com, a menos que o tenha criado em agosto de 2022 ou posterior. Se o usuário tiver uma conta Adobe e não conseguir fazer logon, [envie uma solicitação de suporte](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide) em https://experienceleague.adobe.com/home?lang=pt-BR#support e forneça os detalhes (Motivo do problema = Gerenciamento do usuário).
1. O usuário deve acessar https://accounts.magento.cloud.
1. Depois disso, você poderá adicionar o usuário ao projeto. Para obter etapas, consulte [Adicionar usuários e gerenciar o acesso](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html?lang=pt-BR#add-users-and-manage-access) em nosso Guia de Infraestrutura do Commerce na Nuvem.

## Leitura relacionada:

* [Gerenciar o acesso do usuário](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html?lang=pt-BR) em nosso Guia do Commerce na Infraestrutura em Nuvem.
* [Não é possível fazer logon no suporte da Adobe Commerce ou na conta de nuvem](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/unable-to-log-in-to-support-or-cloud-project.html?lang=pt-BR)
