---
title: Não é possível alterar o Mecanismo de pesquisa usando o Administrador do Commerce (o menu Mecanismo de pesquisa está inacessível)
description: Este artigo fornece uma solução para alterar o Mecanismo de pesquisa do Adobe Commerce usando o Administrador do Commerce se o campo Mecanismo de pesquisa não for exibido ou a caixa de seleção Usar valor do sistema estiver acinzentada e inacessível.
exl-id: 5b0f728c-6a8d-446d-9553-5abc3d01e516
feature: Admin Workspace, Search, Variables
role: Developer
source-git-commit: e9f009cf4e072dcd9784693c10a4c16746af3cc5
workflow-type: tm+mt
source-wordcount: '842'
ht-degree: 0%

---

# Não é possível alterar o Mecanismo de pesquisa usando o Administrador do Commerce (o menu Mecanismo de pesquisa está inacessível)

>[!WARNING]
>
> [O mecanismo de pesquisa do catálogo MySQL será removido no Adobe Commerce 2.4.0](/help/announcements/adobe-commerce-announcements/mysql-catalog-search-engine-will-be-removed-in-magento-2-4-0.md). Você deve ter o Elasticsearch host configurado antes de instalar a versão 2.4.0.
> 
> Consulte:
> [Instalar e configurar o Elasticsearch](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/service/elasticsearch).
> [Instalar e configurar o Opensearch](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/service/opensearch)
> [Instalar e configurar o Live Search](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/live-search/install)

Este artigo fornece uma solução para alterar o mecanismo de pesquisa do Adobe Commerce usando o administrador do Commerce se a variável **Mecanismo de pesquisa** não for exibido ou o campo **Usar valor do sistema** está acinzentada e não está acessível.

Neste artigo:

* [Versões afetadas](#affected-versions)
* [Alterar mecanismo de pesquisa usando o administrador do Commerce (etapas)](#change-search-engine-using-magento-admin-steps)
* [Problemas com o Adobe Commerce no local](#magento-commerce-on-premise)
* [Adobe Commerce na infraestrutura em nuvem](#magento-commerce-cloud)

## Versões afetadas

* Adobe Commerce no local: 2.4.X
* Adobe Commerce na infraestrutura em nuvem:
   * Versão: 2.4.X
   * Arquitetura do plano Starter e Pro
* MySQL, Elasticsearch, Opensearch, Live Search: todas as versões compatíveis

## Alterar mecanismo de pesquisa usando o Administrador (etapas)

1. Faça logon no Admin como Administrador.
1. Na barra lateral Admin do lado esquerdo, clique em **Lojas**. Em seguida, em **Configurações**, escolha **Configuração**.
1. No painel à esquerda, em **Catálogo,** escolher **Catálogo**.
1. Expanda a **Pesquisa no catálogo** seção.    ![catalog_menu.png](assets/catalog_menu.png)
1. Vá para a **Mecanismo de pesquisa** e remova a seleção do campo **Usar valor do sistema** caixa de seleção
1. Clique em **Mecanismo de pesquisa** e selecione uma das opções disponíveis.    ![search_engine_menu.png](assets/search_engine_menu.png)
1. Clique em **Salvar configuração** no canto superior direito da página.

## Problemas com o Adobe Commerce no local

### Problema 1: o campo Mecanismo de pesquisa não é exibido

Ao acessar o **Pesquisa no catálogo** seção, a variável **Mecanismo de pesquisa** não é exibido.

![search_engine_not_displayed.png](assets/search_engine_not_displayed.png)

### Causa: o Modo de Exibição de Armazenamento não é uma Configuração Padrão

A Exibição de loja para o Administrador foi definida com qualquer valor diferente de *Configuração padrão*.

O mecanismo de pesquisa é um conjunto de configurações globais no nível do aplicativo, não no Escopo da Loja. As lojas em um aplicativo do Adobe Commerce não podem usar mecanismos de pesquisa diferentes.

### Solução: defina a exibição da loja para a configuração padrão

1. Faça logon no Admin como Administrador.
1. Na barra lateral Admin do lado esquerdo, clique em **Lojas**. Em seguida, em **Configurações**, escolha **Configuração**.
1. No canto superior esquerdo, clique na guia **Exibição da loja** seletor e escolha *Configuração padrão*.
1. Clique em **OK** na caixa de diálogo de confirmação para aprovar a alteração da exibição de loja.

![change_store_view.png](assets/change_store_view.png)

**Documentação relacionada:** [Alterando Escopo](https://experienceleague.adobe.com/docs/commerce-admin/config/scope-change.html#set-the-scope) em nosso guia do usuário.

### Problema 2: Não é possível desmarcar a opção &quot;Usar valor do sistema&quot;

Ao acessar o **Pesquisa no catálogo** seção do Administrador, a variável **Usar valor do sistema** está acinzentada para que você não possa remover a seleção da caixa de seleção para alterar posteriormente o mecanismo de pesquisa.

### Causa

O mecanismo de pesquisa padrão foi configurado no nível de configuração do aplicativo no `app/etc/env.php` ou `app/etc/config.php` e, portanto, não podem ser alteradas usando a função Admin.

Exemplo da seção com a configuração do mecanismo de pesquisa padrão:

```php
'system'=>
array (
'default'=>
array (
'catalog'=>
array (
'search'=>
array (
'engine'=>'mysql',
),
),
),
),
```

### Solução

Remova a seção com a configuração de mecanismo de pesquisa padrão da `app/etc/env.php` ou o `app/etc/config.php` arquivos de configuração.

### Artigos relacionados em nossa documentação para desenvolvedores

[Arquivos de configuração do Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/files/deployment-files.html) no Guia de configuração do Adobe Commerce

## Adobe Commerce na infraestrutura em nuvem

A alternância de mecanismos de pesquisa usando o Administrador não está disponível no Adobe Commerce na infraestrutura em nuvem devido à forma como a infraestrutura em nuvem foi organizada.

Durante o processo de implantação, os scripts de implantação do Adobe Commerce na infraestrutura em nuvem verificam se o Elasticsearch foi declarado na variável `MAGENTO_CLOUD_RELATIONSHIPS` variável. Se declarado, o Elasticsearch será selecionado como o mecanismo de pesquisa ativo e configurado automaticamente; a variável [Mecanismo de pesquisa MySQL](/help/announcements/adobe-commerce-announcements/mysql-catalog-search-engine-will-be-removed-in-magento-2-4-0.md) fica inacessível no Administrador. Se a relação de Elasticsearch não tiver sido declarada, o MySQL será definido como ativo e o Elasticsearch ficará inacessível.

Não é recomendável editar a variável `app/etc/env.php` ou o `app/etc/config.php` arquivos de configuração diretamente no seu ambiente de nuvem; é por isso que alterar esses arquivos para fazer com que o mecanismo Elasticsearch seja exibido no Administrador (a solução recomendada na seção anterior) não se aplica ao seu projeto de nuvem.

### Alterar mecanismo de pesquisa em ambientes de preparo e produção

Antes de alternar o mecanismo de pesquisa do MySQL para o Elasticsearch em seus ambientes de preparo e produção, verifique se você já [enviou um tíquete de suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) solicitando a ativação do Elasticsearch no ambiente e o tíquete foi resolvido com sucesso.

Para alterar o mecanismo de pesquisa usado em seus ambientes de Preparo e Produção, altere a variável `SEARCH_CONFIGURATION` variável de ambiente no `.magento.env.yaml` no ambiente local e, em seguida, enviar as alterações para os ambientes de Integração e Preparo/Produção para que as alterações entrem em vigor.

Se você estiver alternando para o Elasticsearch 7, a variável SEARCH\_CONFIGURATION no `.magento.env.yaml` O arquivo pode ter a seguinte aparência:

```yaml
stage:
  deploy:
   SEARCH_CONFIGURATION:
     engine: elasticsearch7
     elasticsearch_server_hostname: hostname
     elasticsearch_server_port: '12345'
     elasticsearch_index_prefix: magento
     elasticsearch_server_timeout: '15'
```

Se estiver alternando para [Opensearch (nas versões 2.4.6 e posteriores,)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/elasticsearch/search-engine-shown-elasticsearch-despite-open-search) a variável SEARCH\_CONFIGURATION no `.magento.env.yaml` O arquivo pode ter a seguinte aparência:

```yaml
stage:
  deploy:
   SEARCH_CONFIGURATION:
     engine: opensearch
     elasticsearch_server_hostname: hostname
     elasticsearch_server_port: '12345'
     elasticsearch_index_prefix: magento
     elasticsearch_server_timeout: '15'
```

Se você estiver [alternar para o Live Search](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/error-opensearch-search-engine-doesnt-exist-falling-back-to-livesearch), a variável SEARCH\_CONFIGURATION no `.magento.env.yaml` O arquivo pode ter a seguinte aparência:

```yaml
stage:
  deploy:
   SEARCH_CONFIGURATION:
     engine: livesearch
```

### Documentação relacionada

#### Knowledge base de suporte

* [Habilitar o Elasticsearch na nuvem](/help/how-to/general/enable-elasticsearch-on-cloud.md)

#### Documentação do desenvolvedor

* [Configurar serviço Elasticsearch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/elasticsearch.html)
* [Criar e implantar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/configure-env-yaml.html) (documentação sobre o `.magento.env.yaml` arquivo de configuração)
* [Implantar variáveis](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html) ([seção SEARCH\_CONFIGURATION](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#search_configuration))
* [Serviços](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/services-yaml.html) (documentação sobre o `.magento/services.yaml` arquivo de configuração)
* [Live Search](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/live-search/overview)
