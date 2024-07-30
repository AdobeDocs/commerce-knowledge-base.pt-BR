---
title: Os perfis do cliente não aparecem no Experience Platform
description: Este artigo fornece etapas de solução de problemas se os dados de perfil do cliente não estiverem aparecendo no Experience Platform ao usar a extensão  [!DNL Data Connection] .
feature: Personalization, Integration, Configuration
role: Admin, Developer
source-git-commit: a520ef45f1c55dbf34a98c4f4d3ab49814535434
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 0%

---

# Os perfis do cliente não aparecem no Experience Platform

Este artigo fornece etapas de solução de problemas se os dados de perfil do cliente não estiverem aparecendo no Experience Platform ao usar a extensão Conexão de dados.

## Produtos e versões afetados

* Adobe Commerce 2.4.x com extensão [!DNL Data Connection] instalada

## Problema

Você instalou e configurou a extensão [[!DNL Data Connection]](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/data-connection/overview) e habilitou os dados de perfil do cliente para serem enviados ao Experience Platform, mas esses dados de perfil não estão aparecendo no Experience Platform.

## Solução

Se as informações de perfil do cliente não estiverem aparecendo no Experience Platform, verifique o seguinte:

### Confirme se a versão mais recente do [!DNL Data Connection] está instalada

Verifique se você instalou a versão mais recente da extensão `experience-platform-connector`.

Consulte as [[!DNL Data Connection] notas de versão da extensão](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/data-connection/release-notes) para obter informações sobre a versão mais recente.

>[!NOTE]
>
>A versão mais recente da extensão [!DNL Data Connection] inclui o módulo `customers-connector`, que é responsável por enviar dados de perfil ao Experience Platform. O módulo `customers-connector` deve ser da versão `1.2.0` ou superior.

### Confirme se o módulo do conector do cliente está configurado

Confirme se o módulo `customers-connector` está configurado com base no seu cenário de instalação.

#### Infraestrutura do Adobe Commerce na nuvem

1. Habilitar a variável global `ENABLE_EVENTING` em `.magento.env.yaml`. [Saiba mais](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-global).

   ```bash
       stage:
           global:
               ENABLE_EVENTING: true
   ```

1. Confirme e envie por push os arquivos atualizados para o ambiente em nuvem. Quando a implantação for concluída, habilite o envio de eventos com o seguinte comando:

   ```bash
       bin/magento config:set adobe_io_events/eventing/enabled 1
   ```

#### Instalação local do Adobe Commerce

Execute os seguintes comandos para habilitar a geração de código e os Eventos do Adobe Commerce:

```bash
   bin/magento events:generate:module
   bin/magento module:enable Magento_AdobeCommerceEvents
   bin/magento setup:upgrade
   bin/magento setup:di:compile
   bin/magento config:set adobe_io_events/eventing/enabled 1
```

### Confirme se você ativou os dados do perfil para serem capturados e enviados para o Experience Platform

No Administrador do Commerce, verifique se os seguintes campos estão definidos:

* Em **[!UICONTROL System]** > **[!UICONTROL Services]** > **[!UICONTROL Data Connection]**, verifique se as caixas de seleção [!UICONTROL Back office events] e [!UICONTROL Customer profiles] estão habilitadas.
* Verifique se o campo *[!UICONTROL Profile Dataset ID]* está correto e se é um conjunto de dados diferente do que você está usando atualmente para dados de evento comportamentais e de back-office.

### Verificar se os eventos estão sendo roteados para preparo ou produção

1. Execute o seguinte comando para mostrar o ambiente Adobe Developer atual:

   ```bash
   Copy code
   bin/magento config:show
   adobe_io_events/integration/adobe_io_environment
   ```

1. Se o ambiente estiver definido como *[!UICONTROL Stage]*, altere-o para *[!UICONTROL Production]* com o seguinte comando:

   ```bash
   Copy code
   bin/magento config:set adobe_io_events/integration/adobe_io_environment
   production
   ```

### Tabela SaaS de dados do evento de consulta

Conecte e execute a seguinte consulta SQL para verificar se os registros de perfil do cliente aparecem no
Tabela `event_data_saas` e que não há erros:

```sql
Copy code
select * from event_data_saas;
```

### Lidar com erros de publicação de eventos

1. Se você encontrar o seguinte erro, verifique se a sandbox e as chaves do conector SaaS de produção estão corretas:

   ```css
   Copy code
   2024-06-07 14:37:57 | 2024-06-07 14:38:03 | 1 | 0 | Event publishing
   failed: Error code: 403; reason: Forbidden { "error": { "code":
   "Forbidden", "message": "Client ID is invalid", "details": {
   "error_code": "403003" } } }
   ```

1. Vá para a página *[!UICONTROL Commerce Services Connector]* no Admin e verifique se as chaves [!UICONTROL sandbox/production] especificadas estão configuradas corretamente. Além disso, confirme se as configurações da conta do Commerce [!UICONTROL sandbox/production] correspondem às exibidas no [!UICONTROL Commerce Services Connector]. Saiba [mais](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/user-guides/integration-services/saas#apikey).

### Verifique se a ID de serviço está na inclui na lista de permissões e confirme com o suporte da Adobe Commerce

1. Verifique se [!UICONTROL Commerce Services Connector] `serviceId` aparece na inclui na lista de permissões no Adobe Commerce.
1. Entre em contato com o [suporte da Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide) para confirmar o status da inclui na lista de permissões.

## Leitura relacionada

Consulte a extensão [[!DNL Data Connection]](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/data-connection/overview) no guia do usuário de Serviços da Commerce.
