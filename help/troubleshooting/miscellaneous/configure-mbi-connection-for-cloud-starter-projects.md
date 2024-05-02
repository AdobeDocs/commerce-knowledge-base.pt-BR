---
title: Configuração da conexão do Adobe Commerce Intelligence para projetos existentes do Cloud Starter
description: Este artigo fornece uma solução para quando você deseja configurar a conexão do Adobe Commerce Intelligence para um projeto Cloud Starter existente.
feature: Commerce Intelligence
role: Developer
exl-id: 56f6ad64-729d-4e3a-93a9-da1b91bc5c1d
source-git-commit: b75328202952bf4c8f57ddc538b5c9e4318b2001
workflow-type: tm+mt
source-wordcount: '763'
ht-degree: 0%

---

# Configuração da conexão do Adobe Commerce Intelligence para projetos existentes do Cloud Starter

>[!NOTE]
>
>O Adobe Commerce Intelligence era anteriormente conhecido como Magento Business Intelligence (MBI).

Este artigo fornece uma solução para quando você deseja configurar a conexão do Adobe Commerce Intelligence para um projeto Cloud Starter existente.

## Produtos e versões afetados

Adobe Commerce no Cloud Starter (todas as versões)

## Problema

Você deseja configurar a conexão do Commerce Intelligence para um projeto Cloud Starter existente.

>[!NOTE]
>
>O Adobe não é mais compatível com novas assinaturas do Cloud Starter, mas se você tiver um projeto Starter existente, será necessário seguir as etapas fornecidas abaixo para configurar sua conexão.

## Solução

Para ativar os projetos do Commerce Intelligence para Cloud Starter, crie uma conta do Commerce Intelligence, crie uma chave SSH e finalmente se conecte ao banco de dados do Adobe Commerce.

Siga estas etapas:

1. Crie sua conta do Adobe Commerce Intelligence:

   * Ir para [accounts.magento.com/customer/account/login](https://account.magento.com/customer/account/login).
   * Navegue até **[!UICONTROL My Account]** > **[!UICONTROL My MBI Instances]**.
   * Clique em **[!UICONTROL Create Instance]**. Se você não vir esse botão, entre em contato com o Gerente de sucesso do cliente ou o Consultor técnico do cliente.
   * Selecione sua assinatura do Cloud Starter. Se você tiver apenas uma assinatura do Cloud Starter, ela será selecionada automaticamente.
   * Clique em **[!UICONTROL Continue]**.
   * Insira suas informações para criar sua conta.

   ![Criar conta MBI](/help/troubleshooting/miscellaneous/assets/create_mbi_account.png)

   * Vá para a caixa de entrada e verifique o endereço de email.

   ![Verificar endereço de email](/help/troubleshooting/miscellaneous/assets/verify_email_address_mbi.png)

   * Crie uma senha.

   ![Criar uma senha](/help/troubleshooting/miscellaneous/assets/create_password_mbi.png)

   * Depois de criar sua conta, você terá a opção de adicionar usuários à nova conta. Agora é possível adicionar administradores técnicos para executar as etapas a seguir.

   ![Adicionar usuários](/help/troubleshooting/miscellaneous/assets/add_users_mbi.png)

1. Insira informações sobre sua loja para definir suas preferências.

   ![Adicionar informações da loja](/help/troubleshooting/miscellaneous/assets/add_store_info_mbi.png)

   Você precisará coletar algumas informações antes de conectar o banco de dados para a terceira etapa do fluxo de integração. Você preencherá o *[!UICONTROL Connect your database]* página na etapa 9.

1. Crie um usuário dedicado do Commerce Intelligence.

   * Criar um novo usuário em [account.adobe.com](https://account.adobe.com/).
   * Ir para [https://accounts.magento.com/customer/account/](https://accounts.magento.com/customer/account/) para gerar sua conta do Adobe Commerce.
   * Por que um novo usuário? O Adobe Commerce Intelligence precisa de um usuário adicionado ao projeto para buscar continuamente novos dados que serão transferidos para o data warehouse Commerce Intelligence da conta. Este usuário servirá como essa conexão. A adição desse usuário ao projeto será apresentada na etapa 4.
   * O motivo para ter um usuário dedicado do Commerce Intelligence é impedir que o usuário adicionado seja desativado ou excluído inadvertidamente e interromper a conexão do Commerce Intelligence.

1. Adicione o usuário recém-criado ao ambiente primário do projeto como um *Colaborador*.

   ![Adicionar usuário como colaborador](/help/troubleshooting/miscellaneous/assets/contributor_user_mbi.png)

1. Obtenha suas chaves SSH do Commerce Intelligence.

   * Vá para a **[!UICONTROL Connect your database]** página da interface do usuário de configuração do Commerce Intelligence e rolar para baixo até **[!UICONTROL Encryption settings]**.
   * Para o campo, **[!UICONTROL Encryption Type]**, escolha **[!UICONTROL SSH Tunnel]**.
   * Na lista suspensa, é possível copiar e colar a Chave pública do Magento BI Essentials fornecida.

   ![Configurações de criptografia](/help/troubleshooting/miscellaneous/assets/encryption_type_mbi.png)

1. Adicione sua nova chave pública do Magento BI Essentials ao usuário do Commerce Intelligence criado na etapa 5.

   * Ir para [accounts.magento.com/customer/account/login](https://account.magento.com/customer/account/login). Faça logon com as informações de logon da sua conta para o novo usuário do Commerce Intelligence criado. Em seguida, acesse o **[!UICONTROL Account Settings]** guia.
   * Role para baixo na página e expanda o menu suspenso para chaves SSH. Clique em **[!UICONTROL Add a public key]**.

   ![Adicionar uma chave pública](/help/troubleshooting/miscellaneous/assets/add_public_key_mbi.png)

   * Adicione a chave pública SSH do Magento MBI Essentials da parte superior.

   ![Adicionar chave pública SSH](/help/troubleshooting/miscellaneous/assets/add_ssh_key_mbi.png)

1. Forneça as credenciais do MySQL do Business Intelligence Essentials.

   * Atualize seu `.magento/services.yaml`.

   ```
   mysql:
    type: mysql:10.0
    disk: 2048
    configuration:
        schemas:
            - main
        endpoints:
            mysql:
                default_schema: main
                privileges:
                    main: admin
            mbi:
                default_schema: main
                privileges:
                    main: ro
   ```

   * Atualize seu `.magento.app.yaml`.

   ```
   relationships:
            database: "mysql:mysql"
            mbi: "mysql:mbi"
            redis: "redis:redis"
   ```

1. Obtenha informações para conectar seu banco de dados ao Commerce Intelligence.

   Executar `echo $MAGENTO_CLOUD_RELATIONSHIPS | base64 --decode | json_pp` para obter informações sobre como conectar seu banco de dados.

   Você deve receber informações semelhantes à saída abaixo:

   ```
   "mbi" : [
              {
                 "scheme" : "mysql",
                 "rel" : "mbi",
                 "cluster" : "vfbfui4vmfez6-master-7rqtwti",
                 "query" : {
                    "is_master" : true
                 },
                 "ip" : "169.254.169.143",
                 "path" : "main",
                 "host" : "mbi.internal",
                 "hostname" : "3m7xizydbomhnulyglx2ku4wpq.mysql.service._.magentosite.cloud",
                 "username" : "mbi",
                 "service" : "mysql",
                 "port" : 3306,
                 "password" : "[password]"
              }
           ],
   ```

1. Conecte seu banco de dados do Adobe Commerce.

   ![Conectar seu banco de dados do Adobe Commerce](/help/troubleshooting/miscellaneous/assets/connect_magento_database_mbi.png)

   *Entradas*:

   * Nome da integração: [Escolha um nome para a integração.]
   * Host: `mbi.internal`
   * Porta: 3306
   * Nome de usuário: mbi
   * Senha: [senha de entrada fornecida na saída da Etapa 8.]
   * Nome do banco de dados: main
   * Prefixos de tabela: [deixe em branco se não houver prefixos de tabela]

1. Defina seu [!UICONTROL Timezone Settings].

   ![Configurações de fuso horário](/help/troubleshooting/miscellaneous/assets/timezone_settings_mbi.png)

   *Entradas*

   * Banco de dados: Fuso horário: UTC
   * Fuso horário desejado: [Escolha o fuso horário em que deseja que seus dados sejam exibidos.]

1. Obter informações para suas configurações de criptografia.

   * A interface do projeto fornece uma cadeia de caracteres de acesso SSH. Essa string pode ser usada para coletar as informações necessárias para o Endereço remoto e o Nome de usuário na configuração do **[!UICONTROL Encryption settings]**. Selecionar **[!UICONTROL SSH]** para ver seu Nome de usuário e Endereço remoto. A sequência de caracteres de texto antes da variável *@* é seu Nome de usuário e a sequência de texto depois de *@* é o seu endereço remoto.

   ![Acessar site mestre](/help/troubleshooting/miscellaneous/assets/access_site_mbi.png)

1. Informações de entrada para seu [!UICONTROL Encryption Settings].

   ![Configurações de criptografia](/help/troubleshooting/miscellaneous/assets/encryption_type_mbi.png)

   *Entradas*

   * Tipo de criptografia: túnel SSH
   * Endereço remoto: ssh.us-3.magento.cloud
   * Nome de usuário: vfbfui4vmfez6-master-7rqtwti—mymagento
   * Porta: 22

1. Clique em **[!UICONTROL Save Integration]**.
1. Agora você se conectou com êxito à sua conta do Commerce Intelligence Essentials.
1. Se você for um cliente do Adobe Commerce Intelligence Pro, entre em contato com o Gerente de sucesso do cliente ou o Consultor técnico do cliente para coordenar as próximas etapas.
