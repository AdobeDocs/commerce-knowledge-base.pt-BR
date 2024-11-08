---
title: O Google Analytics é desativado após a implantação
description: Este tópico discute uma solução para um problema típico que você pode ter com o Google Analytics durante a implantação.
exl-id: ecf6a277-2dfa-45cf-b86f-9a27f39017f4
feature: Build, Deploy, Variables
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '188'
ht-degree: 0%

---

# O Google Analytics é desativado após a implantação

Este tópico discute uma solução para um problema típico que você pode ter com o Google Analytics durante a implantação.

## Produtos e versões afetados

* Adobe Commerce na infraestrutura em nuvem, todas as versões

## Problema

Ao implantar seu código em ambientes, os scripts de compilação e implantação verificam se a ramificação `master/production/staging` está implantada para manter o Google Analytics habilitado. Ao implantar ramificações de desenvolvimento (ou secundárias) de mestre em ambientes de desenvolvedor (Integração), o script de implantação desativa o Google Analytics.

## Causa

Esse é um recurso destinado a garantir que os dados e as interações do desenvolvedor não sejam enviados para o ou rastreados pelo Google Analytics.

## Solução

Se quiser que o Google Analytics sempre esteja habilitado, defina a variável de implantação `ENABLE_GOOGLE_ANALYTICS = true`, conforme descrito em [Implantar variáveis](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy#enable_google_analytics) na documentação do desenvolvedor.

>[!NOTE]
>
>Estamos cientes de que este artigo ainda pode conter termos de software padrão da indústria que alguns podem achar racistas, sexistas ou opressivos e que podem fazer com que o leitor se sinta ferido, traumatizado ou indesejado. O Adobe está trabalhando para remover esses termos de nosso código, documentação e experiências do usuário.
