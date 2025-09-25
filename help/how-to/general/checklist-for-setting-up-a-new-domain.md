---
title: Lista de verificação para configurar um novo  [!DNL domain]
description: Esta é uma lista de verificação de como configurar um novo [!DNL domain]  no Adobe Commerce na infraestrutura em nuvem.
exl-id: bfe0582d-2c6d-4814-908f-dfd8c898bef7
feature: Cache
source-git-commit: 79195c457bae31f97c2d47e53e2ff84534697d13
workflow-type: tm+mt
source-wordcount: '569'
ht-degree: 0%

---

# Lista de verificação para configurar um novo [!DNL domain]

Esta lista de verificação explica como configurar um novo [!DNL domain] no Adobe Commerce na infraestrutura em nuvem. Ela se aplica se você estiver adicionando um novo domínio ou substituindo o atual. Também se aplica após obter um novo ambiente de preparo (consulte a Etapa 4).

## Produtos e versões afetados

Adobe Commerce na infraestrutura em nuvem, [todas as versões com suporte](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## Como configurar um novo domínio

### Etapa 1 - Isto é para o [!DNL Integration, Staging] ou [!DNL Production environment]?

* **[!DNL Integration]**: [!DNL Custom domains] não são suportados. Em vez disso, você deve usar este método: [Configurar vários sites ou lojas: Configurar a instalação local](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html#add-new-domains) no guia do usuário.
* **[!DNL Staging]**: Ir para **Etapa 2**.
* **[!DNL Production]**: Ir para **Etapa 3**.

### Etapa 2 - [!DNL Staging environment]: você está em [!DNL Pro] ou [!DNL Starter]?

* **[!DNL Pro]**: **Enviar uma solicitação** para adicionar o domínio a [!DNL Fastly, Nginx] e configurar o [!DNL SSL certificate] (bem como o [!DNL Sendgrid domain], se necessário). Depois de configurado, [atualize a [!DNL DNS] configuração com [!DNL development settings]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#update-dns-configuration-with-development-settings).

>[!NOTE]
>
>Para a arquitetura PRO, a adição de um novo domínio exige o envio de uma solicitação de suporte para o Adobe Commerce. Embora alguns clientes possam configurar manualmente o Fastly por meio do Admin Console, isso só se aplica em casos limitados, como quando o domínio não está vinculado a outro serviço ou projeto do Fastly. No entanto, a configuração do Nginx é sempre necessária e essa etapa deve ser realizada pela Adobe. Por causa disso, a abordagem recomendada e mais confiável é enviar um tíquete de suporte e permitir que a Adobe gerencie todo o processo de configuração do domínio.


* **[!DNL Starter]**: não há suporte para [!DNL Custom domains] no ambiente de preparo.

### Etapa 3 - [!DNL Production environment]: você está em [!DNL Pro] ou [!DNL Starter]?

* **[!DNL Pro]**: **Enviar uma solicitação** para adicionar o domínio a [!DNL Fastly, Nginx] e configurar o [!DNL SSL certificate] (como [!DNL Sendgrid domain], se necessário). Depois de configurado, continue para a **Etapa 4**.

>[!NOTE]
>
>Você mesmo pode adicionar o novo [!DNL domain] a [!DNL Fastly] atualizando a configuração no [!DNL Admin] em **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!DNL Fastly Configuration]** > **[!UICONTROL Domains]** [[!DNL Manage domains]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-custom-cache-configuration.html#manage-domains) em nosso guia do usuário.
>
>
>Se não for possível adicionar o domínio, talvez seja devido a um destes motivos:
>
>1. Você está migrando o domínio local para o ambiente de nuvem, que foi configurado no seu próprio serviço [!DNL Fastly]. Nesse caso, envie uma solicitação e solicite a delegação do domínio.
>1. Você está migrando o domínio do Starter para o Pro. Nesse caso, envie um pedido de assistência adicional.

* **[!DNL Starter]**: Adicione o [!DNL domain] ao seu projeto na guia **[!DNL Domains]** e **envie uma solicitação** para fornecer o **[!DNL ACME Challenge Key]** para o [!DNL SSL certificate].

### Etapa 4 - O [!DNL domain] está ativo?

* **SIM**: [Atualize a [!DNL DNS] configuração com [!UICONTROL production] configurações](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/launch/checklist.html#update-dns-configuration-with-production-settings).
* **NÃO**: [Atualize a [!DNL DNS] configuração com [!UICONTROL development] configurações](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#update-dns-configuration-with-development-settings).

### Etapa 5 - Os redirecionamentos de domínio estão configurados em `magento-vars.php`?

Após a configuração do domínio, é necessário [modificar as variáveis](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure-store/multiple-sites#modify-variables) no arquivo `magento-vars.php` para direcionar o domínio para a URL de site/loja apropriada.

### Etapa 6 - A configuração [!DNL domain] foi verificada?

Se você tiver adicionado novos armazenamentos, grupos de lojas e sites em **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL All Stores]** para o(s) novo(s) domínio(s), verifique se as seções a seguir aparecem no arquivo `app/etc/config.php`, por exemplo:

```php
'scopes' => [
    'websites' => [
        'admin' => [
            'website_id' => '0',
            'code' => 'admin',
            'name' => 'Admin',
            'sort_order' => '0',
            'default_group_id' => '0',
            'is_default' => '0',
        ],
        'base' => [
            'website_id' => '1',
            'code' => 'base',
            'name' => 'Main Website',
            'sort_order' => '0',
            'default_group_id' => '1',
            'is_default' => '1',
        ],
        'site2' => [
            'website_id' => '2',
            'code' => 'site2',
            'name' => 'Second Website',
            'sort_order' => '0',
            'default_group_id' => '2',
            'is_default' => '0',
        ],
    ],
    'groups' => [
        0 => [
            'group_id' => '0',
            'website_id' => '0',
            'name' => 'Default',
            'root_category_id' => '0',
            'default_store_id' => '0',
            'code' => 'default',
        ],
        1 => [
            'group_id' => '1',
            'website_id' => '1',
            'name' => 'Main Website Store',
            'root_category_id' => '2',
            'default_store_id' => '1',
            'code' => 'main_website_store',
        ],
        2 => [
            'group_id' => '2',
            'website_id' => '2',
            'name' => 'Second Website Store',
            'root_category_id' => '2',
            'default_store_id' => '2',
            'code' => 'site2store',
        ],
    ],
    'stores' => [
        'admin' => [
            'store_id' => '0',
            'code' => 'admin',
            'website_id' => '0',
            'group_id' => '0',
            'name' => 'Admin',
            'sort_order' => '0',
            'is_active' => '1',
        ],
        'default' => [
            'store_id' => '1',
            'code' => 'default',
            'website_id' => '1',
            'group_id' => '1',
            'name' => 'Default Store View',
            'sort_order' => '0',
            'is_active' => '1',
        ],
        'site2sv' => [
            'store_id' => '2',
            'code' => 'site2sv',
            'website_id' => '2',
            'group_id' => '2',
            'name' => 'Second Website Store view',
            'sort_order' => '0',
            'is_active' => '1',
        ],
    ],
]
```

Isso significa que você configurou o [SCD na Compilação](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/deploy/static-content#setting-the-scd-on-build) executando o comando `config:dump` no pacote `ece-tools` anteriormente.

Se você descobrir que o novo armazenamento/site que você criou não está sendo exibido no arquivo `app/etc/config.php`, execute o comando novamente para sincronizar o arquivo `config.php` com as alterações no banco de dados, confirme o arquivo `config.php` e implante novamente. Isso facilita a implantação de conteúdo estático para o(s) novo(s) armazenamento/site(s) para os caminhos de arquivo apropriados.

## Leitura relacionada

* [Configurar vários sites ou lojas: Adicionar Novo [!DNL Domains]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html#add-new-domains) em nosso guia do usuário.
* [Site não acessível devido ao encobrimento de origem](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26856)
