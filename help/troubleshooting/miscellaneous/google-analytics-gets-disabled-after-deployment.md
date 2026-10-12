---
title: O Google Analytics é desativado após a implantação
description: Este tópico discute uma solução para um problema típico que você pode ter com o Google Analytics durante a implantação.
exl-id: ecf6a277-2dfa-45cf-b86f-9a27f39017f4
feature: Build, Deploy, Variables
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: bcd8874c-7b93-5596-bdaa-22660e84df14
    internal-label: Deploy
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: 8d0b446f-5b16-5a10-b272-01143504a11c
    internal-label: System
subfeature_v2:
  - id: adedf3b3-e153-47a3-ae73-b5d65067b544
    internal-label: Build system
  - id: 2191e157-828a-5358-ad69-ebcaa8402915
    internal-label: Variables
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '203'
ht-degree: 0%
---
# O Google Analytics é desativado após a implantação

Este tópico discute uma solução para um problema típico que você pode ter com o Google Analytics durante a implantação.

## Produtos e versões afetados

* Adobe Commerce na infraestrutura em nuvem, todas as versões

## Problema

Ao implantar seu código em ambientes, os scripts de compilação e implantação verificam se a ramificação `master/production/staging` está implantada para manter o Google Analytics habilitado. Ao implantar ramificações de desenvolvimento (ou secundárias) de mestre em ambientes de desenvolvedor (Integração), o script de implantação desativa o Google Analytics.

## Causa

Esse é um recurso destinado a garantir que os dados e as interações do desenvolvedor não sejam enviados para o Google Analytics, nem rastreados por ele.

## Solução

Se você quiser que o Google Analytics sempre esteja habilitado, defina a variável de implantação `ENABLE_GOOGLE_ANALYTICS = true`, conforme descrito em [Implantar variáveis](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy#enable_google_analytics) na documentação do desenvolvedor.

>[!NOTE]
>
>Estamos cientes de que este artigo ainda pode conter termos de software padrão da indústria que alguns podem achar racistas, sexistas ou opressivos e que podem fazer com que o leitor se sinta ferido, traumatizado ou indesejado. O Adobe está trabalhando para remover esses termos de nosso código, documentação e experiências do usuário.
