---
title: Lista de verificação para configurar um novo [!DNL domain]
description: Esta é uma lista de verificação de como configurar um novo [!DNL domain] no Adobe Commerce na infraestrutura em nuvem.
exl-id: bfe0582d-2c6d-4814-908f-dfd8c898bef7
feature: Cache
source-git-commit: 625ed2c7ab79f7bca9a979903e97c44c875e607c
workflow-type: tm+mt
source-wordcount: '418'
ht-degree: 0%

---

# Lista de verificação para configurar um novo [!DNL domain]

Esta é uma lista de verificação de como configurar um novo [!DNL domain] no Adobe Commerce na infraestrutura em nuvem. Isso se aplica independentemente de você estar tentando simplesmente adicionar um novo domínio ou substituir o domínio atual por um novo.

## Produtos e versões afetados

Adobe Commerce na infraestrutura em nuvem, [todas as versões compatíveis](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## Como configurar um novo domínio

### Etapa 1 - É para o [!DNL Integration, Staging]ou [!DNL Production environment]?

* **[!DNL Integration]**: [!DNL Custom domains] não são compatíveis. Em vez disso, você deve usar este método: [Configurar vários sites ou lojas: configurar instalação local](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html#add-new-domains) em nosso guia do usuário.
* **[!DNL Staging]**: Vá para **Etapa 2**.
* **[!DNL Production]**: Vá para **Etapa 3**.

### Etapa 2 - [!DNL Staging environment]: você está em [!DNL Pro] ou [!DNL Starter]?

* **[!DNL Pro]**: **Enviar uma solicitação** para adicionar o domínio a [!DNL Fastly, Nginx]e configure o [!DNL SSL certificate] (bem como a [!DNL Sendgrid domain], se necessário). Uma vez configurado, [atualizar o [!DNL DNS] configuração com [!DNL development settings]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#update-dns-configuration-with-development-settings).

>[!NOTE]
>
>Você pode adicionar o novo [!DNL domain] para [!DNL Fastly] atualizando a configuração no [!DNL Admin] in **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!DNL Fastly Configuration]** > **[!UICONTROL Domains]** como em [[!DNL Manage domains]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-custom-cache-configuration.html#manage-domains) em nosso guia do usuário.
>
>Se não for possível adicionar o domínio, talvez seja devido a um destes motivos:
>
>1. Você está migrando o domínio para o ambiente de nuvem, que foi configurado em seu próprio [!DNL Fastly] serviço. Nesse caso, envie uma solicitação e solicite a delegação do domínio.
>1. Você está migrando o domínio do Starter para o Pro. Nesse caso, envie um pedido de assistência adicional.

* **[!DNL Starter]**: [!DNL Custom domains] não são compatíveis com o ambiente de preparo.

### Etapa 3 - [!DNL Production environment]: você está em [!DNL Pro] ou [!DNL Starter]?

* **[!DNL Pro]**: **Enviar uma solicitação** para adicionar o domínio a [!DNL Fastly, Nginx]e configure o [!DNL SSL certificate] (como o [!DNL Sendgrid domain], se necessário). Depois de configurado, continue para **Etapa 4**.

>[!NOTE]
>
>Você pode adicionar o novo [!DNL domain] para [!DNL Fastly] atualizando a configuração no [!DNL Admin] in **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!DNL Fastly Configuration]** > **[!UICONTROL Domains]** [[!DNL Manage domains]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-custom-cache-configuration.html#manage-domains) em nosso guia do usuário.
>
>
>Se não for possível adicionar o domínio, talvez seja devido a um destes motivos:
>
>1. Você está migrando o domínio do local para o ambiente de nuvem, que foi configurado em seu próprio [!DNL Fastly] serviço. Nesse caso, envie uma solicitação e solicite a delegação do domínio.
>1. Você está migrando o domínio do Starter para o Pro. Nesse caso, envie um pedido de assistência adicional.

* **[!DNL Starter]**: adicione o [!DNL domain] ao seu projeto no **[!DNL Domains]** , depois **enviar uma solicitação** para fornecer a **[!DNL ACME Challenge Key]** para o [!DNL SSL certificate].

### Etapa 4 - É o [!DNL domain] ao vivo?

* **SIM**: [Atualize o [!DNL DNS] configuração com [!UICONTROL production] configurações](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/launch/checklist.html#update-dns-configuration-with-production-settings).
* **NÃO**: [Atualize o [!DNL DNS] configuração com [!UICONTROL development] configurações](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#update-dns-configuration-with-development-settings).

## Leitura relacionada

* [Configurar vários sites ou lojas: Adicionar novo [!DNL Domains]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html#add-new-domains) em nosso guia do usuário.
