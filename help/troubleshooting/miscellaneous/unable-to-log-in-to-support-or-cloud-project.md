---
title: Não é possível fazer logon no suporte da Adobe Commerce ou na conta da nuvem
description: Este artigo fornece uma solução para quando você luta para fazer logon no suporte da Adobe Commerce ou no seu projeto na nuvem.
exl-id: 676b32d2-8197-4c60-a1b1-3c51b01dd3a3
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
source-wordcount: '276'
ht-degree: 0%
---
# Não é possível fazer logon no suporte da Adobe Commerce ou na conta da nuvem

Este artigo fornece uma solução para quando você luta para fazer logon no suporte da Adobe Commerce ou no seu projeto na nuvem.

## Produtos e versões afetados

Adobe Commerce (todos os métodos de implantação) todas as [versões com suporte](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## Problema

Ao acessar [https://account.magento.com/customer/account/login/](https://account.magento.com/customer/account/login/) ou [https://accounts.magento.cloud/user](https://accounts.magento.cloud/user), você poderá notar que agora há um formulário de logon unificado e que não é mais possível inserir suas credenciais como anteriormente.

<u>Etapas a serem reproduzidas</u>:

Tente fazer logon em sua conta da Commerce.

![adobe-login-one](assets/adobe-login-one.png)

<u>Resultado esperado</u>:

Logon realizado com sucesso.

<u>Resultado real</u>:

Seja redirecionado para uma página para entrar com uma conta da Adobe e as credenciais não funcionarem.

![adobe-login-two](assets/adobe-login-two.png)


## Causa

Como parte do nosso processo de integração do Adobe Commerce com outras soluções da Adobe, todos os usuários precisarão criar um logon do Adobe, caso ainda não tenham um, usando o mesmo endereço de email conectado à sua MageID.

## Solução

Você pode fazer logon na conta com:

- Uma conta corporativa/pessoal existente da Adobe.
- Se você não tiver uma conta do Adobe, crie uma com o mesmo endereço de email.

Para ver as etapas, consulte o [Commerce Identity Manager](https://experienceleague.adobe.com/docs/commerce-admin/start/commerce-account/commerce-identity-manager.html) na Adobe Experience League.

## Leitura relacionada

- [Link Magento.com e logons de conta do accounts.magento.cloud](/help/faq/general/linking-magento-com-and-accounts-magento-cloud-account-logins.md)
