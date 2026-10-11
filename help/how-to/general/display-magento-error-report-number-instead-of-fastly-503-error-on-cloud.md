---
title: Exibir número do relatório de erros do Adobe Commerce em vez do erro Fastly 503
description: 'Por padrão, o Fastly oculta todos os erros do Adobe Commerce atrás do erro **503 Service Unavailable**. Para exibir o número do relatório de log de erros do Adobe Commerce (para encontrá-lo nos logs e ver os detalhes do erro), abra o site omitindo o Fastly usando estas etapas:'
exl-id: c0a4a9f8-a674-4cef-8088-e844594e6076
feature: Cache, Cloud
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 5a951749-fac9-5bc7-9a98-ebe4ff066437
    internal-label: Cloud
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '271'
ht-degree: 0%
---
# Exibir número do relatório de erros do Adobe Commerce em vez do erro Fastly 503

Por padrão, o Fastly oculta todos os erros do Adobe Commerce atrás do erro **503 Serviço Indisponível**. Para exibir o número do relatório de log de erros do Adobe Commerce (para encontrá-lo nos logs e ver os detalhes do erro), abra o site omitindo o Fastly usando estas etapas:

1. Adicione o domínio e o endereço IP do aplicativo ao arquivo de hosts no computador local.
1. Limpe o cache do navegador e os cookies (ou alterne para o modo incógnito).
1. Abra o site da loja novamente para ver o erro de Adobe Commerce.

Depois de ver o erro autêntico do Adobe Commerce e o número do relatório de erros, você pode obter detalhes no arquivo do relatório de erros seguindo estas etapas:

1. SSH para o ambiente afetado. Consulte [SSH para um ambiente](https://experienceleague.adobe.com/pt-br/docs/commerce-cloud-service/user-guide/develop/secure-connections) na documentação do desenvolvedor.
1. Localize o arquivo `./var/report/{error_number}`.

## Adicionar o domínio do aplicativo e o endereço IP ao arquivo de hosts: etapas detalhadas

1. Verifique o IP do servidor do armazenamento executando o comando `nslookup` na linha de comando no computador local:
   * Usuários da arquitetura Pro (ambientes de preparo e produção):

   ```
   nslookup {your_project_id}.ent.magento.cloud
   ```

   * Usuários de arquitetura inicial (todos os ambientes); usuários de arquitetura profissional (ambiente de integração):

   ```
   nslookup gw.{your_region}.magentosite.cloud
   ```

1. Adicione o domínio de armazenamento e o IP do servidor de aplicativos ao arquivo de hosts em seu computador local usando o seguinte formato:

```
{server_IP} {store_domain}
```
