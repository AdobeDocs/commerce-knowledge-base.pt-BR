---
title: Lista de verificação para configurar um novo  [!DNL domain]
description: Esta é uma lista de verificação de como configurar um novo [!DNL domain]  no Adobe Commerce na infraestrutura em nuvem.
exl-id: bfe0582d-2c6d-4814-908f-dfd8c898bef7
feature: Cache
source-git-commit: f7b246088e3580922bd3389b2992e5dd8f97ff7a
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---

# Lista de verificação para configurar um novo [!DNL domain]

Esta lista de verificação explica como configurar um novo [!DNL domain] no Adobe Commerce na infraestrutura em nuvem. Ela se aplica se você estiver adicionando um novo domínio ou substituindo o atual. Também se aplica após obter um novo ambiente de preparo (consulte a Etapa 4).

## Produtos e versões afetados

Adobe Commerce na infraestrutura em nuvem, [todas as versões com suporte](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## Como configurar um novo domínio

### Etapa 1 - Isto é para o [!DNL Integration, Staging] ou [!DNL Production environment]?

* **[!DNL Integration]**: [!DNL Custom domains] não são suportados. Em vez disso, você deve usar este método: [Configurar vários sites ou lojas: Configurar a instalação local](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html?lang=pt-BR#add-new-domains) no guia do usuário.
* **[!DNL Staging]**: Ir para **Etapa 2**.
* **[!DNL Production]**: Ir para **Etapa 3**.

### Etapa 2 - [!DNL Staging environment]: você está em [!DNL Pro] ou [!DNL Starter]?

* **[!DNL Pro]**: **Enviar uma solicitação** para adicionar o domínio a [!DNL Fastly, Nginx] e configurar o [!DNL SSL certificate] (bem como o [!DNL Sendgrid domain], se necessário). Depois de configurado, [atualize a [!DNL DNS] configuração com [!DNL development settings]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html?lang=pt-BR#update-dns-configuration-with-development-settings).

>[!NOTE]
>
>Você mesmo pode adicionar o novo [!DNL domain] a [!DNL Fastly] atualizando a configuração no [!DNL Admin] em **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!DNL Fastly Configuration]** > **[!UICONTROL Domains]** como em [[!DNL Manage domains]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-custom-cache-configuration.html?lang=pt-BR#manage-domains) em nosso guia do usuário.
>
>Se não for possível adicionar o domínio, talvez seja devido a um destes motivos:
>
>1. Você está migrando o domínio para o ambiente de nuvem, que foi configurado no seu próprio serviço [!DNL Fastly]. Nesse caso, envie uma solicitação e solicite a delegação do domínio.
>1. Você está migrando o domínio do Starter para o Pro. Nesse caso, envie um pedido de assistência adicional.

* **[!DNL Starter]**: não há suporte para [!DNL Custom domains] no ambiente de preparo.

### Etapa 3 - [!DNL Production environment]: você está em [!DNL Pro] ou [!DNL Starter]?

* **[!DNL Pro]**: **Enviar uma solicitação** para adicionar o domínio a [!DNL Fastly, Nginx] e configurar o [!DNL SSL certificate] (como [!DNL Sendgrid domain], se necessário). Depois de configurado, continue para a **Etapa 4**.

>[!NOTE]
>
>Você mesmo pode adicionar o novo [!DNL domain] a [!DNL Fastly] atualizando a configuração no [!DNL Admin] em **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!DNL Fastly Configuration]** > **[!UICONTROL Domains]** [[!DNL Manage domains]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-custom-cache-configuration.html?lang=pt-BR#manage-domains) em nosso guia do usuário.
>
>
>Se não for possível adicionar o domínio, talvez seja devido a um destes motivos:
>
>1. Você está migrando o domínio local para o ambiente de nuvem, que foi configurado no seu próprio serviço [!DNL Fastly]. Nesse caso, envie uma solicitação e solicite a delegação do domínio.
>1. Você está migrando o domínio do Starter para o Pro. Nesse caso, envie um pedido de assistência adicional.

* **[!DNL Starter]**: Adicione o [!DNL domain] ao seu projeto na guia **[!DNL Domains]** e **envie uma solicitação** para fornecer o **[!DNL ACME Challenge Key]** para o [!DNL SSL certificate].

### Etapa 4 - O [!DNL domain] está ativo?

* **SIM**: [Atualize a [!DNL DNS] configuração com [!UICONTROL production] configurações](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/launch/checklist.html?lang=pt-BR#update-dns-configuration-with-production-settings).
* **NÃO**: [Atualize a [!DNL DNS] configuração com [!UICONTROL development] configurações](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html?lang=pt-BR#update-dns-configuration-with-development-settings).

## Leitura relacionada

* [Configurar vários sites ou lojas: Adicionar Novo [!DNL Domains]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html?lang=pt-BR#add-new-domains) em nosso guia do usuário.
* [Site não acessível devido ao encobrimento de origem](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/troubleshooting/site-down-or-unresponsive/production-site-not-accessible-due-to-origin-cloaking)
