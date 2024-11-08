---
title: Reorganizar ramificações de nuvem no Adobe Commerce
description: Este artigo fornece as etapas que você pode seguir para reorganizar ramificações de nuvem no Adobe Commerce, se elas não estiverem organizadas de acordo com a hierarquia correta. Se você não tiver as ramificações organizadas na hierarquia correta, não será possível mesclar à ramificação pai correta - ela irá para a ramificação pai existente.
exl-id: 4fc0de96-da66-4634-a38a-6a1536855f8f
feature: Cloud
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 0%

---

# Reorganizar ramificações de nuvem no Adobe Commerce

Este artigo fornece as etapas que você pode seguir para reorganizar ramificações de nuvem no Adobe Commerce, se elas não estiverem organizadas de acordo com a hierarquia correta. Se você não tiver as ramificações organizadas na hierarquia correta, não será possível mesclar à ramificação pai correta - ela irá para a ramificação pai existente.

## Produtos e versões afetados:

* Adobe Commerce na infraestrutura em nuvem, 2.3.0-2.3.7-p2, 2.4.0-2.4.3-p1

## Organização de ramificações na nuvem

A organização de hierarquia correta para suas ramificações é:

* [!DNL Master [main] > Production > Staging > Integration]
* [!DNL Master [main] > Production > Staging > Integration2]

## Solução para organização incorreta de ramificações na nuvem

Para reorganizar ramificações de nuvem:

1. Você deve ter a função [[!DNL Super User]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html).
1. Instale a magento-cloud [!DNL CLI] (se ainda não tiver instalado).
1. Execute o seguinte comando para as ramificações que precisam ser movidas:
   `magento-cloud environment:info -e <branch to move> parent <target parent>`

Nota: Você pode especificar a ramificação pai ao criar uma nova ramificação. Para ver as etapas, consulte [Introdução à criação de ramificações](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/cli-branches) em nossa documentação para desenvolvedores.

Você pode criar uma nova ramificação de ambiente usando o comando de ambiente magento-cloud `branch <environment-name> <parent-environment-ID>`.

Pode levar algum tempo adicional para criar e ativar uma nova ramificação de ambiente.

## Leitura relacionada

[Gerencie ramificações com o [!DNL CLI]](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/cli-branches) em nossa documentação do desenvolvedor.
