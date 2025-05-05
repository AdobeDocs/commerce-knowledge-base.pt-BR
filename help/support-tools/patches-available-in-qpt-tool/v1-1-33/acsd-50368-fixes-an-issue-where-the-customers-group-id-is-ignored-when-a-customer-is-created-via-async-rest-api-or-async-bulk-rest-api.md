---
title: 'ACSD-50368: a group_id dos clientes é ignorada quando um cliente é criado por meio da API REST assíncrona ou da API REST assíncrona em massa'
description: Aplique o patch ACSD-50368 para corrigir o problema do Adobe Commerce em que os clientes group_id são ignorados quando um cliente é criado por meio da API REST assíncrona ou da API REST em massa assíncrona.
feature: REST
role: Admin
exl-id: bad76183-659a-4ba8-a4a8-18ad69e15aac
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '389'
ht-degree: 0%

---

# ACSD-50368: a group_id dos clientes é ignorada quando um cliente é criado por meio da API REST assíncrona ou da API REST assíncrona em massa

O patch ACSD-50368 corrige o problema em que a group_id de clientes é ignorada quando um cliente é criado por meio da API REST assíncrona ou da API REST em massa assíncrona. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.33 está instalado. A ID do patch é ACSD-50368. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3 - 2.4.4-p4

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR>). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A group_id dos clientes é ignorada quando um cliente é criado por meio da API REST assíncrona ou da API REST assíncrona em massa.

<u>Pré-requisitos</u>:

Configure o RabbitMQ para filas de processamento:

```
bin/magento setup:config:set --amqp-host=services --amqp-port=5672 --amqp-user=guest --amqp-password=guest 
bin/magento setup:upgrade --keep-generated
```

<u>Etapas a serem reproduzidas</u>

1. Usar uma solicitação de API Rest assíncrona para criar um cliente:

   ```
   curl --location 'https://site.test/rest/default/async/V1/customers' \
   --header 'Authorization: Bearer eyJraWQiOiIxIiwiYWxnIjoiSFMyNTYifQ.eyJ1aWQiOjEsInV0eXBpZCI6MiwiaWF0IjoxNjc5NDMzNzcxLCJleHAiOjE2Nzk0MzczNzF9.xau6KyILrkdCY_8K8aMlH4TmqcCXdH4Zcst_CLhdxYY' \
   --header 'Content-Type: application/json' \
   --header 'Cookie: PHPSESSID=844fltmqq1g15qe4ju3l00tiai' \
   --data-raw '{
       "customer": {
           "email": "foo@bar.test",
           "firstname": "Test",
           "lastname": "User",
           "group_id": 2
       }
   }
   ```

1. Uma resposta semelhante é retornada:

   ```
   {
       "bulk_uuid": "b101ddcb-b7fd-4208-a2a6-2e84c9e61bcd",
       "request_items": [
           {
               "id": 0,
               "data_hash":   "6e718a93b02a30a98cb994d1c4e8cf1eeedcb962f384e4a463c"   ,
               "status": "accepted"
           }
       ],
       "errors": false
   }
   ```

1. Verifique o status desta solicitação assíncrona:

   ```
   curl --location 'https://site.test/rest/default/V1/bulk/b101ddcb-b7fd-4208-a2a6-2e84c9e61bcd/detailed-status' \
   --header 'Authorization: Bearer eyJraWQiOiIxIiwiYWxnIjoiSFMyNTYifQ.eyJ1aWQiOjEsInV0eXBpZCI6MiwiaWF0IjoxNjc5NDMzNzcxLCJleHAiOjE2Nzk0MzczNzF9.xau6KyILrkdCY_8K8aMlH4TmqcCXdH4Zcst_CLhdxYY' \
   --header 'Cookie: PHPSESSID=844fltmqq1g15qe4ju3l00tiai
   ```

<u>Resultados esperados</u>:

O group_id está definido corretamente como 2 para o novo cliente.

<u>Resultados reais</u>:

O group_id é definido para o padrão 1 para o novo cliente.

```
{
    "operations_list": [
        {
            "id": 0,
            "bulk_uuid": "b101ddcb-b7fd-4208-a2a6-2e84c9e61bcd",
            "topic_name": "async.magento.customer.api.accountmanagementinterface.createaccount.post",
            "serialized_data": null,
            "result_serialized_data": "{\"id\":4,\"group_id\":1,\"created_at\":\"2023-03-21 22:01:09\",\"updated_at\":\"2023-03-21 22:01:09\",\"created_in\":\"Default Store View\",\"email\":\"foo@bar.test\",\"firstname\":\"Test\",\"lastname\":\"User\",\"store_id\":1,\"website_id\":1,\"addresses\":[],\"disable_auto_group_change\":0,\"extension_attributes\":{\"is_subscribed\":false}}",
            "status": 1,
            "result_message": "Service execution success Magento\\Customer\\Model\\AccountManagement\\Interceptor::createAccount",
            "error_code": null
        }
    ],
        "user_type": 2,
        "bulk_id": "b101ddcb-b7fd-4208-a2a6-2e84c9e61bcd",
        "description": "Topic async.magento.customer.api.accountmanagementinterface.createaccount.post",
        "start_time": "2023-03-21 22:01:09",
        "user_id": 1,
        "operation_count": 1
}
```

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] versão: uma nova ferramenta para autoatender patches de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando o [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
