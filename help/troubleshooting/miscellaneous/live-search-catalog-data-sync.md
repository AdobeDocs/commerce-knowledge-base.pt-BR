---
title: Catálogo do Live Search não sincronizado
description: Este artigo fornece soluções para o problema do Adobe Commerce em que os dados do catálogo não são sincronizados corretamente ao usar a extensão do Live Search.
exl-id: cd2e602f-b2c7-4ecf-874f-ec5f99ae1900
feature: Catalog Management, Search
role: Developer
source-git-commit: 96e5bfc677949fb5f925040b95f951ca518fa71a
workflow-type: tm+mt
source-wordcount: '763'
ht-degree: 0%

---

# Catálogo do Live Search não sincronizado

Este artigo fornece soluções para o problema do Adobe Commerce em que os dados do catálogo não são sincronizados corretamente ao usar a extensão do Live Search.

## Produtos e versões afetados

* Adobe Commerce 2.4.x com extensão do Live Search instalada

## Problema

Os dados do catálogo não estão sincronizados corretamente ou um novo produto foi adicionado, mas não aparece nos resultados da pesquisa. Você também pode receber o seguinte erro no `var/log/exception.log`:

`Magento_LiveSearch: An error occurred in search backend. {"result":{"errors":[{"message":"Exception while fetching data (/productSearch) : No index was found for this request"}]}}`

>[!NOTE]
>
>Os nomes de tabela `catalog_data_exporter_products` e `catalog_data_exporter_product_attributes` agora são chamados `cde_products_feed` e `cde_product_attributes_feed` a partir de [!DNL Live Search] versão 4.2.1. Para comerciantes em versões anteriores à 4.2.1, procure os dados nos nomes de tabela antigos, `catalog_data_exporter_products` e `catalog_data_exporter_product_attributes`.

<u>Etapas a serem reproduzidas</u>

1. Configure e conecte o Live Search para sua instância do Adobe Commerce conforme descrito em [Instalar o Live Search > Configurar chaves de API](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html#configure-api-keys) na documentação do usuário.
1. Após 30 minutos, verifique os dados do catálogo exportados conforme descrito em [Instalar Live Search > Verificar exportação](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html#verify-export) na documentação do usuário.
1. Após 30 minutos, teste a conexão conforme descrito em [Instalar Live Search > Testar a conexão](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html#test-connection) na documentação do usuário.

Ou

1. Adicione um novo produto ao catálogo.
1. Tente executar uma consulta de pesquisa usando o nome do produto ou outros atributos pesquisáveis após 15 a 20 minutos a partir do momento em que o indexador de Magento + cron foi executado para sincronizar dados com o serviço de back-end.

<u>Resultado esperado</u>

* Os dados de catálogo exportados podem ser verificados
* Conexão bem-sucedida
* O novo produto é exibido nos resultados da pesquisa.

<u>Resultado real</u>

O catálogo exportado não pode ser verificado e/ou a conexão não foi estabelecida porque a chave de API foi alterada.

## Solução

Você pode realizar várias ações para tentar corrigir os problemas de sincronização do catálogo.

### Aguardar a aplicação das alterações

Após configurar e conectar, pode levar mais de 30 minutos para que o índice em ES (Elasticsearch) seja criado e os resultados da pesquisa sejam retornados. Espera-se que as atualizações de produto únicas subsequentes sejam indexadas em alguns minutos.

### Sincronizar dados do produto para um SKU específico

Se os dados do seu produto não estiverem sincronizados corretamente para uma SKU específica, faça o seguinte:

1. Use a consulta [!DNL SQL] a seguir e verifique se você tem os dados esperados na coluna `feed_data`. Além disso, anote o carimbo de data e hora `modified_at`.

   ```sql
   select * from cde_products_feed where sku = '<your_sku>' and store_view_code = '<your_ store_view_code>';
   ```

1. Se você não vir os dados corretos, tente reindexar usando o seguinte comando e execute novamente a consulta [!DNL SQL] na etapa 1 para verificar os dados:

   ```bash
   bin/magento indexer:reindex cde_products_feed
   ```

1. Se você ainda não vir os dados corretos, [crie um tíquete de Suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

### Verificar carimbo de data e hora da última exportação de produto

1. Se você vir os dados corretos em `cde_products_feed`, use a seguinte consulta [!DNL SQL] para verificar o carimbo de data e hora da última exportação. Deve ser após o carimbo de data/hora `modified_at`:

   ```sql
   select * from scopes_website_data_exporter;
   ```

1. Se o carimbo de data e hora for mais antigo, você poderá aguardar a próxima execução do cron ou acioná-lo sozinho usando o seguinte comando:

   ```bash
   bin/magento cron:run --group=saas_data_exporter
   ```

1. Aguarde `<>` vez (tempo para atualizações incrementais). Se você ainda não visualizar seus dados, [crie um tíquete de Suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

### Sincronizar código de atributo específico

Se os dados do atributo do produto não estiverem sincronizados corretamente para um código de atributo específico, faça o seguinte:

1. Use a consulta [!DNL SQL] a seguir e verifique se você tem os dados esperados na coluna `feed_data`. Além disso, anote o carimbo de data e hora `modified_at`.

   ```sql
   select * from cde_product_attributes_feed where json_extract(feed_data, '$.attributeCode') = '<your_attribute_code>' and store_view_code = '<your_ store_view_code>';
   ```

1. Se você não vir os dados corretos, use o seguinte comando para reindexar e, em seguida, execute novamente a consulta [!DNL SQL] na etapa 1 para verificar os dados.

   ```bash
   bin/magento indexer:reindex cde_product_attributes_feed
   ```

1. Se você ainda não vir os dados corretos, [crie um tíquete de Suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

### Verificar carimbo de data/hora da última exportação de atributo de produto

Se você vir os dados corretos em `cde_product_attributes_feed`:

1. Use a consulta [!DNL SQL] a seguir para verificar o carimbo de data/hora da última exportação. Deve estar após o carimbo de data/hora `modified_at`.

   ```sql
   select * from scopes_website_data_exporter;
   ```

1. Se o carimbo de data e hora for mais antigo, você poderá aguardar a próxima execução do cron ou acioná-lo sozinho usando o seguinte comando:

   ```bash
   bin/magento cron:run --group=saas_data_exporter
   ```

1. Aguarde de 15 a 20 minutos (tempo para atualizações incrementais). Se você ainda não visualizar seus dados, [crie um tíquete de Suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

### Sincronizar após alteração na configuração da API

(Problema conhecido) Se você alterou a configuração da API, o que resulta em uma alteração na ID do espaço de dados e descobriu que as alterações no catálogo não estão mais sincronizadas, execute os seguintes comandos:

```bash
bin/magento saas:resync --feed products
bin/magento saas:resync --feed productattributes
```

Execute os seguintes comandos para ressincronizar os feeds:

```
bin/magento saas:resync --feed productattributes --cleaup-feed
bin/magento saas:resync --feed products --cleanup-feed
bin/magento saas:resync --feed scopesCustomerGroup --cleanup-feed
bin/magento saas:resync --feed scopesWebsite --cleanup-feed
bin/magento saas:resync --feed prices --cleanup-feed
bin/magento saas:resync --feed productOverrides --cleanup-feed
bin/magento saas:resync --feed variants --cleanup-feed
bin/magento saas:resync --feed categories --cleanup-feed
bin/magento saas:resync --feed categoryPermissions --cleanup-feed
```

[Enviar uma solicitação de suporte](https://experienceleague.adobe.com/home?support-tab=home#support) para solicitar a reindexação do índice do Live Search. Na descrição do problema, inclua o espaço de dados/ID do ambiente encontrado no painel de administração em **[!UICONTROL System]** > **[!UICONTROL Services]** > **[!UICONTROL Commerce Services Connector]**.

## Leitura relacionada

* [Integrar o Live Search](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/onboarding-overview.html) na documentação do usuário
* [Revise logs e solucione problemas na exportação e sincronização de dados SaaS do Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/saas-data-export/troubleshooting-logging) no Guia de exportação de dados SaaS do Adobe Commerce
* [Práticas recomendadas para modificar tabelas de banco de dados](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) no Manual de implementação do Commerce
